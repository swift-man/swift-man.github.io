---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "WKWebView Alert Crash"
toc: true
toc_sticky: true
toc_label: 목차
tag: "WKWebView"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-folder-open"
  - title: "UIView"
    url: /ios/uiresponder/uiview/
    icon: "far fa-folder-open"
  - title: "WKWebView"
    url: /ios/uiresponder/uiview/wkwebview/
    icon: "far fa-folder-open"
---
WKWebView를 사용하다보면 종종 아래와 같은 크래시를 발견할 수 있다.  
원인은 Alert를 네이티브에서 띄우고, Alert를 소유한 ViewController 가 dismiss 되면, completionHandler를 리턴하지 못하면서 발생한다.
이것은 CompletionHandlerWrapper 로 방어할 수 있는데, 이러한 치명적 오류는 아래 코드를 통해 방어할 수 있다.

>Fatal Exception: NSInternalInconsistencyException
Completion handler passed to -[UIViewController webView:runJavaScriptAlertPanelWithMessage:initiatedByFrame:completionHandler:] was not called

## WKUIDelegate
```swift
extension UIViewController: WKUIDelegate {
    func webView(_ webView: WKWebView, runJavaScriptAlertPanelWithMessage message: String, initiatedByFrame frame: WKFrameInfo, completionHandler: @escaping () -> Void) {
        guard webView.url?.host != nil else {
            completionHandler()
            return
        }

        let completionHandlerWrapper = CompletionHandlerWrapper(completionHandler: completionHandler, defaultValue: Void())
        let alert = UIAlertController(title: nil,
                                      message: message,
                                      preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: "ok".localized(),
                                      style: .default,
                                      handler: { _ in
                                        completionHandlerWrapper.respondHandler(())
        }))
        
        present(alert, animated: true, completion: nil)
    }

    func webView(_ webView: WKWebView, runJavaScriptConfirmPanelWithMessage message: String, initiatedByFrame frame: WKFrameInfo, completionHandler: @escaping (Bool) -> Void) {
        guard webView.url?.host != nil else {
            completionHandler(false)
            return
        }

        let completionHandlerWrapper = CompletionHandlerWrapper(completionHandler: completionHandler, defaultValue: false)
        let alert = UIAlertController(title: nil, message: message, preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: "cancel".localized(),
                                      style: .cancel,
                                      handler: { _ in
                                        completionHandlerWrapper.respondHandler(false)
        }))

        alert.addAction(UIAlertAction(title: "common.ok".localized(),
                                      style: .default,
                                      handler: { _ in
                                        completionHandlerWrapper.respondHandler(true)
        }))
        
        present(alert, animated: true, completion: nil)
    }
}
```

```swift
public final class CompletionHandlerWrapper<Element> {
    private var completionHandler: ((Element) -> Void)?
    private let defaultValue: Element
    
    public init(completionHandler: @escaping ((Element) -> Void), defaultValue: Element) {
        self.completionHandler = completionHandler
        self.defaultValue = defaultValue
    }
    
    public func respondHandler(_ value: Element) {
        completionHandler?(value)
        completionHandler = nil
    }
    
    deinit {
        respondHandler(defaultValue)
    }
}
```

---
description: This example shows how to integrate the Tiledesk Widget for iOS
---

# Integrate Widget for iOS with WKWebView

## Controller

```text
//
//  WebViewViewController.swift
//  Tiledesk
//
//  Created by Dario De Pascalis on 03/04/2019.
//  Copyright © 2019 tiledesk. All rights reserved.
//

import UIKit
import WebKit

class WebViewViewController: UIViewController, WKUIDelegate {
 
    @IBOutlet weak var webView: WKWebView!
    @IBAction func actionClosing(_ sender: UIBarButtonItem) {
        dismiss(animated: true, completion: nil)
    }
    
    override func loadView() {
        
        let image = UIImage(named: "ic_navigation_bar")!
        let nav = self.navigationController?.navigationBar
        let tintColor = UIColor(red: 51, green: 71, blue: 94, alpha: 1)
        nav?.setupNavigationBar(barStyleBlack: true, tintColor: tintColor, image: image)
        
        
        let webConfiguration = WKWebViewConfiguration()
        webView = WKWebView(frame: .zero, configuration: webConfiguration)
        webView.uiDelegate = self
        view = webView
    }
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        let url = "https://widget.tiledesk.com/v2/index.html?tiledesk_projectid=<CHANGE_IT>&tiledesk_isopen=true&tiledesk_fullscreenMode=true&tiledesk_hideHeaderCloseButton=true"
        let myURL = URL(string:url)
        let myRequest = URLRequest(url: myURL!)
        webView.load(myRequest)
    }
    

    /*
    // MARK: - Navigation

    // In a storyboard-based application, you will often want to do a little preparation before navigation
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        // Get the new view controller using segue.destination.
        // Pass the selected object to the new view controller.
    }
    */

}

```

## Storyboard

```text
<?xml version="1.0" encoding="UTF-8"?>
<document type="com.apple.InterfaceBuilder3.CocoaTouch.Storyboard.XIB" version="3.0" toolsVersion="14490.70" targetRuntime="iOS.CocoaTouch" propertyAccessControl="none" useAutolayout="YES" useTraitCollections="YES" useSafeAreas="YES" colorMatched="YES" initialViewController="CiD-yN-qLJ">
    <device id="retina4_7" orientation="portrait">
        <adaptation id="fullscreen"/>
    </device>
    <dependencies>
        <deployment identifier="iOS"/>
        <plugIn identifier="com.apple.InterfaceBuilder.IBCocoaTouchPlugin" version="14490.49"/>
        <capability name="Safe area layout guides" minToolsVersion="9.0"/>
        <capability name="documents saved in the Xcode 8 format" minToolsVersion="8.0"/>
    </dependencies>
    <scenes>
        <!--Web View View Controller-->
        <scene sceneID="Zr5-Tx-nwy">
            <objects>
                <viewController id="Hzh-EN-76S" customClass="WebViewViewController" customModule="tiledesk" customModuleProvider="target" sceneMemberID="viewController">
                    <view key="view" contentMode="scaleToFill" id="NSp-F1-ZTb">
                        <rect key="frame" x="0.0" y="0.0" width="375" height="603"/>
                        <autoresizingMask key="autoresizingMask" widthSizable="YES" heightSizable="YES"/>
                        <subviews>
                            <wkWebView contentMode="scaleToFill" translatesAutoresizingMaskIntoConstraints="NO" id="L4e-kf-ZZd">
                                <rect key="frame" x="0.0" y="0.0" width="375" height="603"/>
                                <color key="backgroundColor" red="0.36078431370000003" green="0.38823529410000002" blue="0.4039215686" alpha="1" colorSpace="custom" customColorSpace="sRGB"/>
                                <wkWebViewConfiguration key="configuration">
                                    <audiovisualMediaTypes key="mediaTypesRequiringUserActionForPlayback" none="YES"/>
                                    <wkPreferences key="preferences"/>
                                </wkWebViewConfiguration>
                            </wkWebView>
                        </subviews>
                        <color key="backgroundColor" white="1" alpha="1" colorSpace="custom" customColorSpace="genericGamma22GrayColorSpace"/>
                        <constraints>
                            <constraint firstItem="WoG-QX-cga" firstAttribute="trailing" secondItem="L4e-kf-ZZd" secondAttribute="trailing" id="0y5-Wu-r5x"/>
                            <constraint firstItem="L4e-kf-ZZd" firstAttribute="top" secondItem="WoG-QX-cga" secondAttribute="top" id="5EJ-yi-Mm6"/>
                            <constraint firstItem="WoG-QX-cga" firstAttribute="bottom" secondItem="L4e-kf-ZZd" secondAttribute="bottom" id="BUX-aA-cYO"/>
                            <constraint firstItem="L4e-kf-ZZd" firstAttribute="leading" secondItem="WoG-QX-cga" secondAttribute="leading" id="jQw-ri-LWE"/>
                        </constraints>
                        <viewLayoutGuide key="safeArea" id="WoG-QX-cga"/>
                    </view>
                    <navigationItem key="navigationItem" id="gTf-SI-kAh">
                        <barButtonItem key="rightBarButtonItem" systemItem="stop" id="SBc-v7-a1X">
                            <color key="tintColor" white="1" alpha="1" colorSpace="custom" customColorSpace="genericGamma22GrayColorSpace"/>
                            <connections>
                                <action selector="actionClosing:" destination="Hzh-EN-76S" id="vZx-lM-Z2F"/>
                            </connections>
                        </barButtonItem>
                    </navigationItem>
                </viewController>
                <placeholder placeholderIdentifier="IBFirstResponder" id="9rE-nK-POq" userLabel="First Responder" sceneMemberID="firstResponder"/>
            </objects>
            <point key="canvasLocation" x="1196" y="623"/>
        </scene>
        <!--Navigation Controller-->
        <scene sceneID="6X5-8k-QKb">
            <objects>
                <navigationController restorationIdentifier="WebViewID" storyboardIdentifier="WebViewID" automaticallyAdjustsScrollViewInsets="NO" id="CiD-yN-qLJ" sceneMemberID="viewController">
                    <toolbarItems/>
                    <navigationBar key="navigationBar" contentMode="scaleToFill" insetsLayoutMarginsFromSafeArea="NO" barStyle="black" translucent="NO" id="z4M-Pd-FHZ">
                        <rect key="frame" x="0.0" y="20" width="375" height="44"/>
                        <autoresizingMask key="autoresizingMask"/>
                        <color key="barTintColor" red="0.20000000000000001" green="0.2784313725" blue="0.36862745099999999" alpha="1" colorSpace="custom" customColorSpace="sRGB"/>
                    </navigationBar>
                    <nil name="viewControllers"/>
                    <connections>
                        <segue destination="Hzh-EN-76S" kind="relationship" relationship="rootViewController" id="Gqe-q8-lcW"/>
                    </connections>
                </navigationController>
                <placeholder placeholderIdentifier="IBFirstResponder" id="STh-f8-S0g" userLabel="First Responder" sceneMemberID="firstResponder"/>
            </objects>
            <point key="canvasLocation" x="385" y="623"/>
        </scene>
    </scenes>
</document>

```


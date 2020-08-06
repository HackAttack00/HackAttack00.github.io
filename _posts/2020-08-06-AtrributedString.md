---
title: "String에 부분 색깔 및 폰트 입히기"
date: 2020-08-06 22:25:00 -0400
categories: AttributedString font color
---

    func makeEmptyGuideText(label:UILabel?) {
        let font = UIFont(name:"AppleSDGothicNeo-Regular" , size: 14.0)!
        let boldFont = UIFont(name: "AppleSDGothicNeo-Bold", size: 14.0)!
        let attributedStr = NSMutableAttributedString(string: (label?.text)!)
        attributedStr.addAttribute(.font, value: font, range: ((label?.text)! as NSString).range(of: (((label?.text)! as NSString) as String)))
        attributedStr.addAttribute(.foregroundColor, value: RGBA(68, 68, 68, 1), range: ((label?.text)! as NSString).range(of: (((label?.text)! as NSString) as String)))
        attributedStr.addAttribute(.foregroundColor, value: RGBA(66, 121, 255, 1), range: ((label?.text)! as NSString).range(of: "이모티콘"))
        attributedStr.addAttribute(.foregroundColor, value: RGBA(66, 121, 255, 1), range: ((label?.text)! as NSString).range(of: "구매 이모티콘"))
        attributedStr.addAttribute(.font, value: boldFont, range: ((label?.text)! as NSString).range(of: "이모티콘"))
        attributedStr.addAttribute(.font, value: boldFont, range: ((label?.text)! as NSString).range(of: "구매 이모티콘"))
        label?.attributedText = attributedStr
    }

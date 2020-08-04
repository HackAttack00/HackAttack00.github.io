---
title: "iOS keyboard inputview"
date: 2020-07-31 12:43:00 -0400
categories: collectionView
---

iOS keyboard inputView rotation중
override func viewWillTransition(to size: CGSize, with coordinator: UIViewControllerTransitionCoordinator)
이 호출 되지않는 문제가 발생

    NotificationCenter.default.addObserver(self, selector: #selector(readyForMoveOffsetForRotation), name: UIResponder.keyboardWillChangeFrameNotification, object: nil)

    @objc private func readyForMoveOffsetForRotation() {
        self.emoticonSwipingController?.collectionView.collectionViewLayout.invalidateLayout()
    }

키보드 프레임 변경 노티를 등록해서 로테이션시 UI처리를 하여 동작은 하게하였다

하지만 자세히 들여다보면 동작이 자연스럽지는 못하다 ㅜㅜ





---
title: 'Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7dd1723d9d92d9bc1b667cc3fddbc3ea297d8b8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389123"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion

Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung, Ändern der `Publish Version` -Eigenschaft bewirkt, dass die Anwendung als Update veröffentlicht werden. Standardmäßig Visual Studio automatisch inkrementiert die `Revision` Anzahl von der `Publish Version` jedes Mal veröffentlichen Sie die Anwendung.

Sie können dieses Verhalten deaktivieren, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>So deaktivieren Sie automatisch Inkrementieren der Veröffentlichungsversion

1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.

3.  In der **Veröffentlichungsversion** deaktivieren Sie im Abschnitt der **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen** Kontrollkästchen.

## <a name="see-also"></a>Siehe auch

- [How to: Set the ClickOnce publish version (Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion)](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publish ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
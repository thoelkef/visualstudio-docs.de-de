---
title: 'Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea53e5e50aebc7c8ad201f6dae1003350f9fa4e2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633446"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion
Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Eigenschaft bestimmt, ob die Anwendung, die Sie veröffentlichen als Update behandelt wird. Jede Zeitpunktversion erhöht wird, die Anwendung als Update veröffentlicht werden.

 Die `Publish Version` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.

> [!NOTE]
>  Es gibt eine Projektoption, die automatisch erhöht wird die `Publish Version` Eigenschaft jedes Mal die Anwendung veröffentlicht wird; diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: automatisch Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>So ändern Sie die Veröffentlichungsversion

1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.

3.  In **Veröffentlichungsversion** Feld, das Erhöhen der **wichtigen**, **kleinere**, **erstellen**, oder **Revision** Version die Nummern.

    > [!NOTE]
    >  Sie sollten niemals eine Versionsnummer verringern; Dies kann zu unvorhersehbaren Updateverhalten führen.

## <a name="see-also"></a>Siehe auch
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
- [How to: Automatically increment the ClickOnce publish version (Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion)](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publish ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
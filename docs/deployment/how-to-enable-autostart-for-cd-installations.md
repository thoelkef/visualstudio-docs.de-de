---
title: 'Vorgehensweise: Aktivieren von AutoStart für Installationen von CD | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4359b863da56242bbe612fa0055690d9923a9ec4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600474"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Vorgehensweise: Aktivieren von AutoStart für CD-Installationen
Bei der Bereitstellung ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung über Wechselmedien wie z. B. CD-ROM oder DVD-ROM können `AutoStart` , damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird automatisch gestartet, wenn das Medium eingelegt ist.

 `AutoStart` kann aktiviert werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.

### <a name="to-enable-autostart"></a>Aktivieren von AutoStart

1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.

3.  Klicken Sie auf die Schaltfläche **Optionen**.

     Die **Veröffentlichungsoptionen** Dialogfeld wird angezeigt.

4.  Klicken Sie auf **Bereitstellung**.

5.  Wählen Sie die **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** Kontrollkästchen.

     Ein *"Autorun.inf"* Datei wird an den Veröffentlichungsort kopiert werden, wenn die Anwendung veröffentlicht wird.

## <a name="see-also"></a>Siehe auch
- [Publish ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
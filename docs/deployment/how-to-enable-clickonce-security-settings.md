---
title: 'Vorgehensweise: ClickOnce-Sicherheitseinstellungen aktivieren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52acc18aa18873076df3d02071616c0399b1f33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407119"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen
Codezugriffssicherheit für ClickOnce-Anwendungen muss aktiviert sein, um die Anwendung zu veröffentlichen. Dies erfolgt automatisch bei der Veröffentlichung einer Anwendung mithilfe des Veröffentlichungs-Assistenten.

 In einigen Fällen kann die Leistung, die bei der Erstellung oder Debuggen der Anwendung aktivieren auf die Codezugriffssicherheit auswirken werden; in diesen Fällen können Sie die Sicherheitseinstellungen vorübergehend deaktivieren möchten.

 ClickOnce-Sicherheitseinstellungen können aktiviert oder deaktiviert die **Sicherheit** auf der Seite die **Projekt-Designer**.

### <a name="to-enable-clickonce-security-settings"></a>ClickOnce-Sicherheitseinstellungen aktivieren

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Sicherheit** .

3. Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .

     Sie können jetzt die Sicherheitseinstellungen für Ihre Anwendung auf der Seite "Sicherheit" anpassen.

    > [!NOTE]
    > Dieses Kontrollkästchen ausgewählt ist automatisch jedes Mal, die die Anwendung veröffentlicht wird, mit der **veröffentlichen** Assistenten.

### <a name="to-disable-clickonce-security-settings"></a>So deaktivieren Sie die ClickOnce-Sicherheitseinstellungen

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Sicherheit** .

3. Deaktivieren der **Enable ClickOnce Security Settings** Kontrollkästchen.

     Die Anwendung wird mit den Sicherheitseinstellungen für volle Vertrauenswürdigkeit ausgeführt werden; Alle Einstellungen für die **Sicherheit** Seite ignoriert werden.

    > [!NOTE]
    > Jedes Mal, wenn die Anwendung mit dem Webpublishing-Assistenten veröffentlicht wird, wird dieses Kontrollkästchen aktiviert werden; Sie müssen Sie erneut nach jeder erfolgreichen Veröffentlichung löschen.

## <a name="see-also"></a>Siehe auch
- [Secure ClickOnce applications (Sichern von ClickOnce-Anwendungen)](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)

---
title: Aktivieren von AutoStart für CD-Installationen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 28fa4830c3ea5ff840e0d58f6d31f718c28ec3fb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850942"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Vorgehensweise: Aktivieren von AutoStart für CD-Installationen
Beim Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe von Wechselmedien wie CD-ROM oder DVD-ROM können Sie aktivieren, `AutoStart` damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung beim Einfügen des Mediums automatisch gestartet wird.

 `AutoStart` kann auf der Seite **veröffentlichen** des **Projekt-Designers**aktiviert werden.

### <a name="to-enable-autostart"></a>So aktivieren Sie Autostart

1. Wenn ein Projekt in **Projektmappen-Explorer**ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** .

     Das Dialogfeld **Veröffentlichungs Optionen** wird angezeigt.

4. Klicken Sie auf **Bereitstellung**.

5. Aktivieren Sie das Kontrollkästchen **bei CD-Installationen, beim Einfügen der CD automatisch starten** .

     Wenn die Anwendung veröffentlicht wird, wird eine *Autorun. inf* -Datei an den Speicherort der Veröffentlichung kopiert.

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
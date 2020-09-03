---
title: 'Vorgehensweise: Aktivieren von AutoStart für CD-Installationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153785"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Gewusst wie: Aktivieren von AutoStart für Installationen von CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Bereitstellen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung mithilfe von Wechselmedien wie CD-ROM oder DVD-ROM können Sie aktivieren, `AutoStart` damit die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung beim Einfügen des Mediums automatisch gestartet wird.  
  
 `AutoStart` kann auf der Seite **veröffentlichen** des **Projekt-Designers**aktiviert werden.  
  
### <a name="to-enable-autostart"></a>So aktivieren Sie Autostart  
  
1. Wenn ein Projekt in **Projektmappen-Explorer**ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Optionen** .  
  
     Das Dialogfeld **Veröffentlichungs Optionen** wird angezeigt.  
  
4. Klicken Sie auf **Bereitstellung**.  
  
5. Aktivieren Sie das Kontrollkästchen **bei CD-Installationen, beim Einfügen der CD automatisch starten** .  
  
     Wenn die Anwendung veröffentlicht wird, wird eine Autorun. inf-Datei an den Speicherort der Veröffentlichung kopiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

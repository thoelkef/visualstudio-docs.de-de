---
title: 'Vorgehensweise: angeben, auf dem Visual Studio die Dateien kopiert | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 9392686e08048ea88615b927cf942d66a4b9a06c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Gewusst wie: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.  
  
 Können Sie angeben, die `Publish Location` Eigenschaft auf die **veröffentlichen** auf der Seite der **Projekt-Designer**, oder indem Sie den Veröffentlichungs-Assistenten. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Speicherort veröffentlichen** Feld, geben Sie die publishing Speicherort mithilfe einer der folgenden Formate:  
  
    -   Geben Sie den Pfad zum Veröffentlichen in einer Datei Dateifreigabe- oder indem entweder ein UNC-Pfad (\\\Server\ApplicationName) oder einem Dateipfad (C:\Deploy\ApplicationName).  
  
    -   Bei Veröffentlichung auf einem FTP-Server geben Sie den Pfad im Format "ftp://ftp.microsoft.com/Anwendungsname" ein.  
  
     Beachten Sie, dass im Text vorhanden sein muss die **Veröffentlichungsort** Feld in der Reihenfolge für die Schaltfläche zum Durchsuchen (**...** ) zu arbeiten.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
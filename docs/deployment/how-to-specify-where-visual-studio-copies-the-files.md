---
title: "How to: Specify Where Visual Studio Copies the Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publishing, specifying location"
  - "Publish Location property"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify Where Visual Studio Copies the Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden.  Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP\-Server handeln.  
  
 Sie können die Eigenschaft `Publish Location` auf der Seite **Veröffentlichen** des **Projekt\-Designers** oder mit dem Webpublishing\-Assistenten festlegen.  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort.  Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
### So legen Sie einen Veröffentlichungsort fest  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen\-Explorer** im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Geben Sie in das Feld **Ort der Veröffentlichung** den Ort für die Veröffentlichung in einem der folgenden Formate ein:  
  
    -   Geben Sie den Pfad zum Veröffentlichen in einer Dateifreigabe oder unter einem Datenträgerpfad mit einem UNC\-Pfad \(\\\\Server\\Anwendungsname\) oder mit einem Dateipfad \(C:\\Deploy\\Anwendungsname\) ein.  
  
    -   Bei Veröffentlichung auf einem FTP\-Server geben Sie den Pfad im Format "ftp:\/\/ftp.microsoft.com\/Anwendungsname" ein.  
  
     Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen \(**...**\) funktioniert.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
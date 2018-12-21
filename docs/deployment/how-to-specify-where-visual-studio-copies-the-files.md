---
title: Geben Sie den Speicherort zum Kopieren von Dateien | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4154f7b3a148968347b39911b9a7e9c28830eac
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068314"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.  
  
 Sie können die Eigenschaft `Publish Location` auf der Seite **Veröffentlichen** des **Projekt-Designers** oder mit dem Webpublishing-Assistenten festlegen. Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Geben Sie in das Feld **Ort der Veröffentlichung** den Ort für die Veröffentlichung in einem der folgenden Formate ein:  
  
   - Geben Sie den Pfad zum Veröffentlichen in einer Dateifreigabe oder unter einem Datenträgerpfad als UNC-Pfad (*\\\Server\ApplicationName*) oder Dateipfad (*C:\Deploy\ApplicationName*) ein.  
  
   - Geben Sie den Pfad zum Veröffentlichen auf einem FTP-Server im Format <em>ftp://ftp.microsoft.com/\<ApplicationName></em> ein.  
  
     Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen (**...**) funktioniert.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
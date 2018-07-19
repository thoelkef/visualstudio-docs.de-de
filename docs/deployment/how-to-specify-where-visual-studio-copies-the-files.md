---
title: 'Vorgehensweise: angeben, in denen Visual Studio die Dateien kopiert | Microsoft-Dokumentation'
ms.custom: ''
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
ms.openlocfilehash: 2b2a4d642bc551127f34fe7a64ec01665b7ace70
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078627"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Gewusst wie: angeben, in denen Visual Studio die Dateien kopiert
Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.  
  
 Können Sie angeben, die `Publish Location` Eigenschaft für die **veröffentlichen** auf der Seite die **Projekt-Designer**, oder mit dem Webpublishing-Assistenten. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Speicherort veröffentlichen** Geben Sie den Ort der Veröffentlichung mit einem der folgenden Formate:  
  
    -   Um auf einen Dateifreigabe- oder Dateipfad veröffentlichen, geben Sie den Pfad mit einem UNC-Pfad (*\\\Server\ApplicationName*) oder einen Dateipfad (*C:\Deploy\ApplicationName*).  
  
    -   Um auf einem FTP-Server veröffentlichen, geben Sie den Pfad im Format *ftp://ftp.microsoft.com/\<ApplicationName >*.  
  
     Beachten Sie, dass Text angegeben sein, muss die **Veröffentlichungsort** Feld in der Reihenfolge für die Schaltfläche zum Durchsuchen (**...** ) Schaltfläche funktioniert.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
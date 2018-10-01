---
title: 'Vorgehensweise: angeben, in denen Visual Studio die Dateien kopiert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 52f19317bbfad963dd5bc4dc3e540640f9234c12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522252"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Gewusst wie: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: angeben, in denen Visual Studio die Dateien kopiert](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-where-visual-studio-copies-the-files).  
  
Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.  
  
 Können Sie angeben, die `Publish Location` Eigenschaft für die **veröffentlichen** auf der Seite die **Projekt-Designer**, oder mit dem Webpublishing-Assistenten. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Speicherort veröffentlichen** Geben Sie den Ort der Veröffentlichung mit einem der folgenden Formate:  
  
    -   Um auf einen Dateifreigabe- oder Dateipfad veröffentlichen, geben Sie den Pfad mit einem UNC-Pfad (\\\Server\ApplicationName) oder einen Dateipfad (C:\Deploy\ApplicationName).  
  
    -   Bei Veröffentlichung auf einem FTP-Server geben Sie den Pfad im Format "ftp://ftp.microsoft.com/Anwendungsname" ein.  
  
     Beachten Sie, dass Text angegeben sein, muss die **Veröffentlichungsort** Feld in der Reihenfolge für die Schaltfläche zum Durchsuchen (**...** ) Schaltfläche funktioniert.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)




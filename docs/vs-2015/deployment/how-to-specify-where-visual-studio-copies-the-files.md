---
title: 'Gewusst wie: Angeben des Orts, an dem Visual Studio 2015 Dateien kopiert | Microsoft-Dokumentation'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226160"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Gewusst wie: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.

 Sie können die Eigenschaft `Publish Location` auf der Seite **Veröffentlichen** des **Projekt-Designers** oder mit dem Webpublishing-Assistenten festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Geben Sie in das Feld **Ort der Veröffentlichung** den Ort für die Veröffentlichung in einem der folgenden Formate ein:

   - Geben Sie zum Veröffentlichen in einer Dateifreigabe oder einem Datenträger Pfad den Pfad entweder mithilfe eines UNC-Pfads ( \\ \server\applicationname) oder eines Dateipfads (c:\Deploy\ApplicationName) ein.

   - Um auf einem FTP-Server zu veröffentlichen, geben Sie den Pfad im Format ftp: \/ /FTP.Microsoft.com/ApplicationName ein.

     Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen (**...**) funktioniert.

## <a name="see-also"></a>Weitere Informationen
 Veröffentlichen von [ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md) Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Webpublishing-Assistenten

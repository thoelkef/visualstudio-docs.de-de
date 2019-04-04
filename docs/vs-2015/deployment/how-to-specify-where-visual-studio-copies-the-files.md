---
title: 'Vorgehensweise: Legen Sie fest, in denen Dateien von Kopien von Visual Studio 2015 | Microsoft-Dokumentation'
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
ms.openlocfilehash: 6b9f44f3d4f1a9d1b110501d0178e0e2e8dc4e47
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961525"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer Anwendung mithilfe von ClickOnce, gibt die Eigenschaft `Publish Location` den Speicherort an, unter dem die Anwendungsdateien und das Anwendungsmanifest abgelegt werden. Dabei kann es sich um einen Dateipfad oder den Pfad zu einem FTP-Server handeln.

 Sie können die Eigenschaft `Publish Location` auf der Seite **Veröffentlichen** des **Projekt-Designers** oder mit dem Webpublishing-Assistenten festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Publish a ClickOnce Application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

### <a name="to-specify-a-publishing-location"></a>So legen Sie einen Veröffentlichungsort fest

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Geben Sie in das Feld **Ort der Veröffentlichung** den Ort für die Veröffentlichung in einem der folgenden Formate ein:

   - Um auf einen Dateifreigabe- oder Dateipfad veröffentlichen, geben Sie den Pfad mit einem UNC-Pfad (\\\Server\ApplicationName) oder einen Dateipfad (C:\Deploy\ApplicationName).

   - Bei Veröffentlichung auf einem FTP-Server geben Sie den Pfad im Format "ftp://ftp.microsoft.com/Anwendungsname" ein.

     Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen (**...**) funktioniert.

## <a name="see-also"></a>Siehe auch
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md) [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

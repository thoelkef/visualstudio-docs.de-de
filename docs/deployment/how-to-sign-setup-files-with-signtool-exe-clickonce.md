---
title: 'Vorgehensweise: Signieren von Setupdateien mit SignTool.exe (ClickOnce) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081500"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Gewusst wie: Signieren von Setupdateien mit SignTool.exe (ClickOnce)
Sie können *SignTool.exe* sich ein Setupprogramm (*setup.exe*). Durch diesen Prozess können Sie sicherstellen, dass manipulierte Dateien nicht auf den Computern von Endbenutzern installiert werden.  
  
 Standardmäßig verfügt ClickOnce über signierte Manifeste und ein signiertes Setupprogramm. Wenn Sie jedoch später die Parameter des Setupprogramms ändern möchten, müssen Sie das Setupprogramm später signieren. Wenn Sie die Parameter nach dem Signieren des Setupprogramms ändern, wird die Signatur beschädigt.  
  
 Mit dem folgenden Verfahren werden nicht signierte Manifeste und ein nicht signiertes Setupprogramm erstellt. Dann wird das Signieren mit ClickOnce in Visual Studio aktiviert, um signierte Manifeste zu generieren. Das Setupprogramm bleibt nicht signiert, damit der Kunde die ausführbare Datei mit einem eigenen Zertifikat signieren kann.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>So generieren Sie ein nicht signiertes Setupprogramm und signieren es später  
  
1.  Installieren Sie das Zertifikat, mit dem Sie das Manifest signieren möchten, auf dem Entwicklungscomputer.  
  
2.  Wählen Sie das Projekt in **Projektmappen-Explorer**.  
  
3.  Auf der **Projekt** Menü klicken Sie auf *ProjectName* **Eigenschaften**.  
  
4.  In der **Signierung** deaktivieren **ClickOnce-Manifeste signieren**.  
  
5.  In der **veröffentlichen** auf **Voraussetzungen**.  
  
6.  Stellen Sie sicher, dass alle erforderlichen Komponenten ausgewählt sind, und klicken Sie dann auf **OK**.  
  
7.  In der **veröffentlichen** Seite, überprüfen Sie die veröffentlichungseinstellungen aus, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
     Die Projektmappe veröffentlicht das nicht signierte Anwendungsmanifest, das nicht signierte Bereitstellungsmanifest, versionsspezifische Dateien und das nicht signierte Setupprogramm im Pfad des Veröffentlichungsordners.  
  
8.  In der **veröffentlichen** auf **Voraussetzungen**.  
  
9. In der **Voraussetzungen** Dialogfeld das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen**.  
  
10. In der **veröffentlichen** Seite, überprüfen Sie die veröffentlichungseinstellungen aus, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
     Die Projektmappe veröffentlicht das signierte Anwendungsmanifest, das signierte Bereitstellungsmanifest und versionsspezifische Dateien im Pfad des Veröffentlichungsordners. Das nicht signierte Setupprogramm wird durch die Veröffentlichung nicht überschrieben.  
  
11. Öffnen Sie auf der Kundenwebsite eine Eingabeaufforderung.  
  
12. Ändern Sie in das Verzeichnis mit dem *.exe* Datei.  
  
13. Vorzeichen der *.exe* -Datei mit den folgenden Befehl aus:  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Verwenden Sie beispielsweise einen der folgenden Befehle, um das Setupprogramm zu signieren:  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Signieren Sie Anwendungs- und Bereitstellungsmanifeste erneut](../deployment/how-to-re-sign-application-and-deployment-manifests.md)

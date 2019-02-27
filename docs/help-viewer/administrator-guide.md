---
title: Administratorhandbuch für Help Viewer
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21497404d6cdad3f55bffd97fd0329d76418b313
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841574"
---
# <a name="help-viewer-administrator-guide"></a>Administratorhandbuch für Help Viewer

Der Help Viewer ermöglicht das Verwalten der lokal installierten Hilfe in Netzwerkumgebungen mit oder ohne Internetzugriff. Der Inhalt der lokalen Hilfe wird pro Computer konfiguriert. Standardmäßig benötigen Benutzer Administratorrechte, um ihre lokal installierte Hilfe zu aktualisieren.

Wenn Clients in Ihrer Netzwerkumgebung Internetzugriff haben, können Sie mit der ausführbaren Datei des **Hilfeinhalts-Managers** lokale Hilfeinhalte über das Internet bereitstellen. Weitere Informationen zur Befehlszeilensyntax von *HlpCtntMgr.exe* finden Sie unter [Befehlszeilenargumente für den Hilfeinhalts-Manager](../help-viewer/command-line-arguments.md).

Weitere Informationen zum Generieren von Inhalten, zum Erstellen eines Endpunkts für den Intranetdienst und zu ähnlichen Aktionen finden Sie unter [Microsoft Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Wenn Clients in Ihrer Netzwerkumgebung keinen Internetzugriff haben, ermöglicht der Help Viewer das Bereitstellen lokaler Hilfeinhalte über das Intranet oder eine Netzwerkfreigabe. Sie können die Hilfeoptionen der Visual Studio-IDE auch mithilfe von [Überschreibungen von Registrierungsschlüsseln](../help-viewer/behavior-overrides.md) z.B. für Funktionen deaktivieren:

- Online- vs. Offlinehilfe

- Installation von Inhalten beim ersten Start der IDE

- Angeben eines Inhaltsdiensts für das Intranet

- Verwalten von Inhalten

## <a name="deploy-local-help-content-from-the-internet"></a>Bereitstellen lokaler Hilfeinhalte über das Internet

Mit dem **Hilfeinhalts-Manager** (*HlpCtntMgr.exe*) lassen sich lokale Hilfeinhalte über das Internet auf Clientcomputern bereitstellen. Verwenden Sie folgende Syntax:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Weitere Informationen zur Befehlszeilensyntax von *HlpCtntMgr.exe* finden Sie unter [Befehlszeilenargumente für den Hilfeinhalts-Manager](../help-viewer/command-line-arguments.md).

Anforderungen:

-   Clientcomputer müssen Zugriff auf das Internet haben.

-   Benutzer müssen über Administratorrechte verfügen, um lokale Hilfeinhalte nach der Installation aktualisieren, hinzufügen oder entfernen zu können.

Zu beachten:

-   Die Hilfe bleibt standardmäßig online gespeichert.

### <a name="example"></a>Beispiel

Im folgenden Beispiel werden englische Inhalte für Visual Studio auf einem Clientcomputer installiert.

#### <a name="to-install-english-content-from-the-internet"></a>So installieren Sie englischsprachige Inhalte über das Internet

1.  Klicken Sie auf **Start** und dann auf **Ausführen**.

2.  Geben Sie folgenden Pfad ein:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Drücken Sie die **EINGABETASTE**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Bereitstellen der vorinstallierten lokalen Hilfeinhalte auf Clientcomputern

Sie können Inhalte von einem Onlinespeicherort auf einem Computer installieren und die Inhalte anschließend auf andere Computer kopieren.

Anforderungen:

-   Der Computer, auf dem Sie den Inhalt installieren, muss mit dem Internet verbunden sein.

-   Benutzer müssen über Administratorrechte verfügen, um lokale Hilfeinhalte nach der Installation aktualisieren, hinzufügen oder entfernen zu können.

    > [!TIP]
    > Wenn Benutzer nicht über Administratorrechte verfügen, wird empfohlen, die Registerkarte **Inhalt verwalten** im Help Viewer zu deaktivieren. Weitere Informationen finden Sie unter [Überschreibungen durch den Hilfeinhalts-Manager](../help-viewer/behavior-overrides.md).

Zu beachten:

-   Die Hilfe bleibt standardmäßig online gespeichert.

### <a name="create-the-content-set"></a>Erstellen der Inhalte

Bevor Sie die grundlegenden Inhalte erstellen können, müssen Sie alle lokalen Visual Studio-Inhalte auf dem Zielcomputer deinstallieren.

#### <a name="to-uninstall-local-help"></a>So deinstallieren Sie die lokale Hilfe

1. Klicken Sie in Help Viewer auf die Registerkarte **Inhalt verwalten**.

2. Navigieren Sie zu den Visual Studio-Dokumenten.

3. Klicken Sie neben den einzelnen Unterelementen auf **Entfernen**.

4. Klicken Sie zum Deinstallieren auf **Aktualisieren**.

5. Navigieren Sie zu *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15*, und überprüfen Sie, ob der Ordner nur die Datei *catalogType.xml* enthält.

   Nachdem Sie alle zuvor installierten lokalen Visual Studio-Hilfeinhalte entfernt haben, können Sie die grundlegenden Inhalte herunterladen.

#### <a name="to-download-the-content"></a>So laden Sie die Inhalte herunter

1.  Klicken Sie in Help Viewer auf die Registerkarte **Inhalt verwalten**.

2.  Navigieren Sie unter **Empfohlene Dokumentation** oder **Verfügbare Dokumentation** zu den Dokumentationen, die Sie herunterladen möchten, und klicken Sie auf **Hinzufügen**.

3.  Klicken Sie auf **Aktualisieren**.

Anschließend müssen Sie den Inhalt so verpacken, dass er auf Clientcomputern bereitgestellt werden kann.

#### <a name="to-package-the-content"></a>So verpacken Sie die Inhalte

1.  Erstellen Sie einen Ordner, um die Inhalte zur späteren Bereitstellung zu kopieren. Beispiel: *C:\VSHelp*.

2.  Öffnen Sie *cmd.exe* mit Administratorberechtigungen.

3.  Navigieren Sie zu dem in Schritt 1 erstellten Ordner.

4.  Geben Sie folgenden Pfad ein:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Beispiel: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Bereitstellen der Inhalte

1.  Erstellen Sie eine Netzwerkfreigabe, und kopieren Sie die Hilfeinhalte dorthin.

     Kopieren Sie beispielsweise den Inhalt von *C:\VSHelp* nach *\\\myserver\VSHelp*.

2.  Erstellen Sie eine *BAT-Datei* für das Bereitstellungsskript für den Hilfeinhalt. Da auf dem Client eine Lesesperre für die im Rahmen des Push-Vorgangs gelöschten Dateien eingerichtet sein könnte, sollte der Client heruntergefahren werden, bevor Sie Updates per Push übertragen. Beispiel:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3.  Führen Sie die *BAT-Datei* auf den lokalen Computern aus, auf denen Sie die Hilfeinhalte installieren möchten.

## <a name="see-also"></a>Siehe auch

- [Befehlszeilenargumente für den Hilfeinhalts-Manager](../help-viewer/command-line-arguments.md)
- [Überschreibungen durch den Hilfeinhalts-Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
- [Microsoft Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)
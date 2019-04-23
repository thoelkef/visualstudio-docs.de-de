---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87bf42ccb44c170321f36a9fe2fa7f44e274dcfe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099662"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung
Jede ClickOnce-Anwendung basierend auf einer *.exe* Datei im Hintergrund installiert und aktualisiert, indem ein individuelles Installationsprogramm erstellt. Ein individuelles Installationsprogramm erstellt kann benutzerdefinierte Benutzeroberfläche während der Installation, einschließlich der benutzerdefinierten Dialogfelder für Sicherheit und Wartung Vorgänge implementieren. Um die Installation erforderlichen Vorgänge ausführen, das benutzerdefinierte Installationsprogramm verwendet die <xref:System.Deployment.Application.InPlaceHostingManager> Klasse. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie ein benutzerdefiniertes Installationsprogramm erstellen, das eine ClickOnce-Anwendung im Hintergrund installiert wird.

## <a name="prerequisites"></a>Vorraussetzungen

### <a name="to-create-a-custom-clickonce-application-installer"></a>Erstellen ein benutzerdefiniertes Installers der ClickOnce-Anwendung

1. Fügen Sie Verweise auf "System.Deployment" und "System.Windows.Forms" hinzu, in der ClickOnce-Anwendung.

2. Fügen Sie eine neue Klasse zu Ihrer Anwendung, und geben Sie einen beliebigen Namen. In dieser exemplarischen Vorgehensweise wird der Name `MyInstaller` verwendet.

3. Fügen Sie die folgenden `Imports` oder `using` Anweisungen am Anfang Ihrer neuen Klasse.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Fügen Sie die folgenden Methoden der Klasse.

     Diese Methoden rufen <xref:System.Deployment.Application.InPlaceHostingManager> Verfahren zum Herunterladen von des Bereitstellungsmanifests, assert berechtigt, den Benutzer für die Berechtigung zur Installation herunter und installieren Sie die Anwendung in die ClickOnce-Cache. Ein individuelles Installationsprogramm erstellt kann angeben, dass eine ClickOnce-Anwendung bereits vertrauenswürdig ist, oder kann die Entscheidung über die Vertrauenswürdigkeit zu verzögern der <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> Methodenaufruf. Dieser Code, stuft die Anwendung.

    > [!NOTE]
    >  Berechtigungen, die von bereits vertrauen darf die Berechtigungen des Codes benutzerdefiniertes Installationsprogramm nicht überschreiten.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Rufen Sie die Installation aus dem Code versucht, den `InstallApplication` Methode. Wenn Sie die Klasse mit dem Namen z. B. `MyInstaller`, möglicherweise rufen Sie `InstallApplication` auf folgende Weise.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Nächste Schritte
 Eine ClickOnce-Anwendung kann auch benutzerdefinierte Logik für Updates, einschließlich einer benutzerdefinierten Benutzeroberfläche anzuzeigenden während des Updates hinzufügen. Weitere Informationen finden Sie unter <xref:System.Deployment.Application.UpdateCheckInfo>. Eine ClickOnce-Anwendung kann auch die standardmäßigen, Verknüpfung und Software -Eintrag mithilfe Unterdrücken einer `<customUX>` Element. Weitere Informationen finden Sie unter [ \<EntryPoint >-Element](../deployment/entrypoint-element-clickonce-application.md) und <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
- [\<EntryPoint >-Element](../deployment/entrypoint-element-clickonce-application.md)
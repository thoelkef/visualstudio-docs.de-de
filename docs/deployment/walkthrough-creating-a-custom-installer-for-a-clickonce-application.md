---
title: "Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung | Microsoft Docs"
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
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 3b6a7069b520c1c4834ee3ca1a5824660803a665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung
Alle ClickOnce-Anwendung auf Grundlage eine .exe-Datei kann werden im Hintergrund installiert und durch ein benutzerdefiniertes Installationsprogramm aktualisiert. Ein benutzerdefiniertes Installationsprogramm kann benutzerdefinierte Benutzeroberfläche während der Installation, einschließlich der benutzerdefinierten Dialogfelder für Sicherheit und Wartungsvorgänge implementieren. Zum Ausführen der Installation erforderlichen Vorgänge benutzerdefinierte Installer nutzt die <xref:System.Deployment.Application.InPlaceHostingManager> Klasse. Diese exemplarische Vorgehensweise veranschaulicht, wie ein benutzerdefiniertes Installationsprogramm erstellen, das eine ClickOnce-Anwendung im Hintergrund installiert wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>So erstellen ein benutzerdefiniertes Installationsprogramm der ClickOnce-Anwendung  
  
1.  Fügen Sie in der ClickOnce-Anwendung Verweise auf "System.Deployment" und "System.Windows.Forms".  
  
2.  Die Anwendung eine neue Klasse hinzu, und geben Sie einen beliebigen Namen. In dieser exemplarischen Vorgehensweise verwendet den Namen `MyInstaller`.  
  
3.  Fügen Sie die folgenden `Imports` oder `using` -Anweisungen an den Anfang der neuen Klasse.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Fügen Sie die folgenden Methoden der Klasse hinzu.  
  
     Diese Methoden aufrufen <xref:System.Deployment.Application.InPlaceHostingManager> Methoden, um das Bereitstellungsmanifest herunterzuladen assert entsprechende Berechtigungen verfügen, fordern Sie den Benutzer für die Berechtigung zum Installieren und herunter, und installieren die Anwendung in den ClickOnce-Cache. Ein benutzerdefiniertes Installationsprogramm kann angeben, dass eine ClickOnce-Anwendung ist bereits vertrauenswürdig, kann die Entscheidung über die Vertrauenswürdigkeit zu verzögern der <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> -Methodenaufruf. Dieser Code stuft die Anwendung.  
  
    > [!NOTE]
    >  Berechtigungen zuweist, vorab vertrauen darf nicht die Berechtigungen des Codes benutzerdefinierter Installer überschreiten.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Aufrufen, um die Installation aus dem Code versucht, die `InstallApplication` Methode. Angenommen, wenn Sie eine Klasse mit dem Namen `MyInstaller`, rufen Sie möglicherweise `InstallApplication` auf folgende Weise.  
  
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
 Eine ClickOnce-Anwendung kann auch benutzerdefinierte Logik für Updates, einschließlich einer benutzerdefinierten Benutzeroberfläche während des Aktualisierungsvorgangs anzuzeigende hinzufügen. Weitere Informationen finden Sie unter <xref:System.Deployment.Application.UpdateCheckInfo>. Eine ClickOnce-Anwendung kann auch die standardmäßigen, Verknüpfung und Software -Eintrag mithilfe Unterdrücken einer `<customUX>` Element. Weitere Informationen finden Sie unter [ \<EntryPoint >-Element](../deployment/entrypoint-element-clickonce-application.md) und <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)   
 [\<EntryPoint >-Element](../deployment/entrypoint-element-clickonce-application.md)
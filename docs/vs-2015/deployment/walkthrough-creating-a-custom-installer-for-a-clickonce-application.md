---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebde75fdf36c84f40ae660a24d469c36e72ceaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841187"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jede ClickOnce-Anwendung, die auf einer exe-Datei basiert, kann im Hintergrund durch ein benutzerdefiniertes Installationsprogramm installiert und aktualisiert werden. Ein benutzerdefiniertes Installationsprogramm kann während der Installation benutzerdefinierte Benutzeroberflächen implementieren, einschließlich benutzerdefinierter Dialogfelder für Sicherheits-und Wartungsvorgänge. Zum Ausführen von Installations Vorgängen verwendet das benutzerdefinierte Installationsprogramm die- <xref:System.Deployment.Application.InPlaceHostingManager> Klasse. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines benutzerdefinierten Installationsprogramms, das eine ClickOnce-Anwendung im Hintergrund installiert.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>So erstellen Sie einen benutzerdefinierten ClickOnce-Anwendungsinstaller  
  
1. Fügen Sie in ihrer ClickOnce-Anwendung Verweise auf "System. Deployment" und "System. Windows. Forms" hinzu.  
  
2. Fügen Sie der Anwendung eine neue Klasse hinzu, und geben Sie einen beliebigen Namen an. In dieser exemplarischen Vorgehensweise wird der Name `MyInstaller` verwendet.  
  
3. Fügen Sie die folgende- `Imports` oder- `using` Anweisung am Anfang der neuen Klasse hinzu.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4. Fügen Sie der-Klasse die folgenden Methoden hinzu.  
  
     Diese Methoden aufrufen <xref:System.Deployment.Application.InPlaceHostingManager> Methoden, um das Bereitstellungs Manifest herunterzuladen, die entsprechenden Berechtigungen zu bestätigen, den Benutzer zur Installation der Berechtigung aufzufordern und die Anwendung dann herunterzuladen und in den ClickOnce-Cache zu installieren. Ein benutzerdefiniertes Installationsprogramm kann angeben, dass eine ClickOnce-Anwendung vorab vertrauenswürdig ist, oder die Entscheidung über die Vertrauenswürdigkeit auf den <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> Methoden aufzurufen. Mit diesem Code wird die Anwendung vorab vertraut.  
  
    > [!NOTE]
    > Die durch die vorvertrauenden Berechtigungen zugewiesenen Berechtigungen dürfen die Berechtigungen des benutzerdefinierten Installationscodes nicht überschreiten.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5. Um zu versuchen, eine Installation aus Ihrem Code durchführen, müssen `InstallApplication` Sie die- Wenn Sie z. b. Ihre Klasse benannt `MyInstaller` haben, können Sie `InstallApplication` auf die folgende Weise aufzurufen.  
  
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
 Eine ClickOnce-Anwendung kann auch benutzerdefinierte Aktualisierungs Logik hinzufügen, einschließlich einer benutzerdefinierten Benutzeroberfläche, die während des Aktualisierungs Vorgangs angezeigt werden soll. Weitere Informationen finden Sie unter <xref:System.Deployment.Application.UpdateCheckInfo>. Eine ClickOnce-Anwendung kann auch den Standardeintrag für das Start Menü, die Verknüpfung und den Eintrag "Software" mit einem-Element unterdrücken `<customUX>` . Weitere Informationen finden Sie unter [ \<entryPoint> Element](../deployment/entrypoint-element-clickonce-application.md) und <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint>-Element](../deployment/entrypoint-element-clickonce-application.md)

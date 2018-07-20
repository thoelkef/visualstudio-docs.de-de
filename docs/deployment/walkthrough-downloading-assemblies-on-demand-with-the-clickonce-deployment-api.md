---
title: 'Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de6698f6e635a151a0f78eecbb90f4d7bd525969
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151274"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung
Standardmäßig alle Assemblys enthalten, in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung werden heruntergeladen, wenn die Anwendung zuerst ausgeführt wird. Allerdings müssen Sie Teile Ihrer Anwendung möglicherweise, die durch eine kleine Gruppe von Benutzern verwendet werden. In diesem Fall soll eine Assembly erst heruntergeladen werden, wenn eine der in ihr definierten Typen erstellt wird. Die folgende exemplarische Vorgehensweise veranschaulicht, wie Sie bestimmte Assemblys in Ihrer Anwendung als "optional" markieren und zum Herunterladen mithilfe von Klassen der <xref:System.Deployment.Application> Namespace verwenden, wenn die common Language Runtime (CLR) angefordert.  
  
> [!NOTE]
>  Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie benötigen eine der folgenden Komponenten in dieser exemplarischen Vorgehensweise benötigt:  
  
-   Das Windows SDK. Das Windows SDK kann aus dem Microsoft Download Center heruntergeladen werden.  
  
-   Visual Studio.  
  
## <a name="create-the-projects"></a>Erstellen Sie die Projekte  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Zum Erstellen eines Projekts, das eine bedarfsabhängige Assembly verwendet.  
  
1.  Erstellen Sie ein Verzeichnis namens ClickOnceOnDemand.  
  
2.  Öffnen Sie das Windows SDK-Eingabeaufforderung oder die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung.  
  
3.  Wechseln Sie zum Verzeichnis ClickOnceOnDemand.  
  
4.  Generieren Sie ein öffentliches/privates Schlüsselpaar mit dem folgenden Befehl ein:  
  
    ```cmd  
    sn -k TestKey.snk  
    ```  
  
5.  Verwenden Sie Editor oder einem anderen Text-Editor, definieren Sie eine Klasse, die mit dem Namen `DynamicClass` mit einer einzelnen Eigenschaft mit dem Namen `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Speichern Sie den Text als eine Datei namens *ClickOnceLibrary.cs* oder *ClickOnceLibrary.vb*, abhängig von der Sprache, die Sie verwenden, zu der *ClickOnceOnDemand* Verzeichnis.  
  
7.  Kompilieren Sie die Datei in eine Assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Um den öffentlichen Schlüssel für die Assembly Sicherheitstoken abzurufen, verwenden Sie den folgenden Befehl aus:  
  
    ```cmd  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Erstellen Sie eine neue Datei mit Ihren Text-Editor, und geben Sie den folgenden Code. Dieser Code erstellt eine Windows Forms-Anwendung, die die ClickOnceLibrary Assembly heruntergeladen wird, wenn dies erforderlich ist.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Suchen Sie im Code den Aufruf von <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Legen Sie`PublicKeyToken` auf den Wert an, die Sie zuvor abgerufen haben.  
  
12. Speichern Sie die Datei entweder als *"Form1.cs"* oder *Form1.vb*.  
  
13. Kompilieren Sie ihn in eine ausführbare Datei mit dem folgenden Befehl aus.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="mark-assemblies-as-optional"></a>Markieren von Assemblys als optional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>So markieren Assemblys als optional klicken Sie in der ClickOnce-Anwendung mit MageUI.exe  
  
1.  Mithilfe von *MageUI.exe*, erstellen Sie ein Anwendungsmanifest, wie im [Exemplarische Vorgehensweise: Manuelles bereitstellen eine ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Anwendungsmanifest:  
  
    -   Nennen Sie das Anwendungsmanifest `ClickOnceOnDemand`.  
  
    -   Auf der **Dateien** auf der Seite die *ClickOnceLibrary.dll* Zeile, legen Sie die **Dateityp** Spalte **keine**.  
  
    -   Auf der **Dateien** auf der Seite die *ClickOnceLibrary.dll* Zeile, und geben `ClickOnceLibrary.dll` in die **Gruppe** Spalte.  
  
2.  Mithilfe von *MageUI.exe*, erstellen Sie ein Bereitstellungsmanifest, wie im [Exemplarische Vorgehensweise: Manuelles bereitstellen eine ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Bereitstellungsmanifest aus:  
  
    -   Nennen Sie das Bereitstellungsmanifest `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testen der neuen assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>So testen Sie die bedarfsabhängige Assembly  
  
1.  Hochladen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung auf einem Webserver.  
  
2.  Starten Sie die Anwendung mit bereitgestellten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] über einen Webbrowser durch Eingeben der URL auf das Bereitstellungsmanifest. Wenn Sie aufrufen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung `ClickOnceOnDemand`, und Sie sie in das Stammverzeichnis von "adatum.com" hochladen, die URL sieht wie folgt:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Wenn das Hauptformular angezeigt wird, drücken Sie die <xref:System.Windows.Forms.Button>. Eine Zeichenfolge in einem Meldungsfeldfenster sollte angezeigt werden, die "Hello, World!" liest.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>
---
title: "Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "assemblies, downloading [ClickOnce]"
  - "ClickOnce deployment, on-demand download"
  - "on-demand assemblies, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig werden alle in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung enthaltenen Assemblys beim ersten Ausführen der Anwendung heruntergeladen.  Möglicherweise werden aber bestimmte Teile der Anwendung nur von wenigen Benutzern verwendet.  In diesem Fall ist es sinnvoll, eine Assembly erst dann herunterzuladen, wenn Sie einen der zugehörigen Typen erstellen.  Die folgende exemplarische Vorgehensweise zeigt, wie Sie bestimmte Assemblys einer Anwendung als "optional" markieren und wie Sie diese unter Verwendung von Klassen im <xref:System.Deployment.Application>\-Namespace herunterladen, wenn sie von der Common Language Runtime \(CLR\) angefordert werden.  
  
> [!NOTE]
>  Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie eine der folgenden Komponenten:  
  
-   Windows SDK.  Das Windows SDK kann aus dem Microsoft Download Center heruntergeladen werden.  
  
-   Visual Studio.  
  
## Erstellen der Projekte  
  
#### So erstellen Sie ein Projekt mit einer bedarfsgesteuerten Assembly  
  
1.  Erstellen Sie ein Verzeichnis mit dem Namen ClickOnceOnDemand.  
  
2.  Öffnen Sie die Windows SDK\-Eingabeaufforderung oder die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Eingabeaufforderung.  
  
3.  Wechseln Sie zum ClickOnceOnDemand\-Verzeichnis.  
  
4.  Generieren Sie mit dem folgenden Befehl ein Schlüsselpaar aus öffentlichem und privatem Schlüssel:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Definieren Sie in Editor oder einem anderen Text\-Editor eine Klasse mit dem Namen `DynamicClass` und einer einzelnen Eigenschaft mit dem Namen `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Speichern Sie den Text je nach verwendeter Sprache als Datei mit dem Namen `ClickOnceLibrary.cs` oder `ClickOnceLibrary.vb` im ClickOnceOnDemand\-Verzeichnis.  
  
7.  Kompilieren Sie die Datei in eine Assembly.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Um das öffentliche Schlüsseltoken für die Assembly abzurufen, verwenden Sie den folgenden Befehl:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Erstellen Sie eine neue Datei im Text\-Editor, und geben Sie den folgenden Code ein.  Durch diesen Code wird eine Windows Forms\-Anwendung erstellt, durch die die ClickOnceLibrary\-Assembly, falls angefordert, heruntergeladen wird.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Suchen Sie im Code den Aufruf von <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Legen Sie `PublicKeyToken` auf den zuvor abgerufenen Wert fest.  
  
12. Speichern Sie die Datei entweder als `Form1.cs` oder `Form1.vb`.  
  
13. Kompilieren Sie sie mit dem folgenden Befehl in eine ausführbare Datei.  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Markieren von Assemblys als optional  
  
#### So markieren Sie Assemblys in der ClickOnce\-Anwendung mit MageUI.exe als optional  
  
1.  Erstellen Sie unter Verwendung von MageUI.exe ein Anwendungsmanifest, wie in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) beschrieben.  Verwenden Sie die folgenden Einstellungen für das Anwendungsmanifest:  
  
    -   Nennen Sie das Anwendungsmanifest `ClickOnceOnDemand`.  
  
    -   Legen Sie auf der Seite **Dateien** in der Zeile für die ClickOnceLibrary.dll die Spalte **Dateityp** auf **Keine** fest.  
  
    -   Geben Sie auf der Seite **Dateien** in der Zeile für die ClickOnceLibrary.dll in der Spalte **Gruppe** den Namen `ClickOnceLibrary.dll` ein.  
  
2.  Verwenden Sie MageUI.exe, um ein Bereitstellungsmanifest zu erstellen, wie in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) beschrieben.  Verwenden Sie die folgenden Einstellungen für das Bereitstellungsmanifest:  
  
    -   Nennen Sie das Bereitstellungsmanifest `ClickOnceOnDemand`.  
  
## Testen der neuen Assembly  
  
#### So testen Sie die bedarfsabhängige Assembly  
  
1.  Laden Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung auf einen Webserver herauf.  
  
2.  Starten Sie die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitgestellte Anwendung über einen Webbrowser, indem Sie die URL zum Bereitstellungsmanifest eingeben.  Wenn Sie der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung den Namen `ClickOnceOnDemand` geben und sie in das Stammverzeichnis von adatum.com heraufladen, sieht die URL folgendermaßen aus:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Wenn das Hauptformular angezeigt wird, klicken Sie auf den <xref:System.Windows.Forms.Button>.  Nun sollte in einem Meldungsfenster die Zeichenfolge "Hello, World\!" angezeigt werden.  
  
## Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>
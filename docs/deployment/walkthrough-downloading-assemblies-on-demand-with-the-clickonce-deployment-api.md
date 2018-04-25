---
title: 'Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung | Microsoft Docs'
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
ms.openlocfilehash: 48ed3828f70424ee328c1fc52873e1a0f7e620aa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung
Standardmäßig alle Assemblys im enthalten eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung werden heruntergeladen, wenn die Anwendung zuerst ausgeführt wird. Allerdings müssen Sie Teile der Anwendung möglicherweise, die von einer kleinen Gruppe Ihrer Benutzer verwendet werden. In diesem Fall soll eine Assembly erst heruntergeladen werden, wenn eine der in ihr definierten Typen erstellt wird. Die folgende exemplarische Vorgehensweise veranschaulicht, wie Sie bestimmte Assemblys in der Anwendung als "optional" markieren und zum Herunterladen dieser mithilfe von Klassen der <xref:System.Deployment.Application> -Namespace, wenn die common Language Runtime (CLR) angefordert.  
  
> [!NOTE]
>  Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Eine der folgenden Komponenten zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie:  
  
-   Das Windows SDK. Das Windows SDK kann aus dem Microsoft Download Center heruntergeladen werden.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Um ein Projekt zu erstellen, die eine Assembly bei Bedarf verwendet.  
  
1.  Erstellen Sie ein Verzeichnis mit dem Namen ClickOnceOnDemand.  
  
2.  Öffnen Sie das Windows SDK-Eingabeaufforderung oder die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung.  
  
3.  Wechseln Sie zum Verzeichnis ClickOnceOnDemand.  
  
4.  Generieren Sie ein öffentliches/privates Schlüsselpaar mit dem folgenden Befehl ein:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Mit dem Editor oder einem anderen Text-Editor, definieren Sie eine Klasse, die mit dem Namen `DynamicClass` mit einer einzelnen Eigenschaft mit dem Namen `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Speichern Sie den Text als eine Datei namens `ClickOnceLibrary.cs` oder `ClickOnceLibrary.vb`, abhängig von der Sprache, die Sie verwenden, die ClickOnceOnDemand-Verzeichnis.  
  
7.  Kompilieren Sie die Datei in eine Assembly ein.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Um den öffentlichen Schlüssel für die Assembly token zu erhalten, verwenden Sie den folgenden Befehl ein:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Erstellen Sie eine neue Datei mit dem Text-Editor, und geben Sie den folgenden Code. Dieser Code erstellt eine Windows Forms-Anwendung, die die ClickOnceLibrary Assembly heruntergeladen wird, wenn dies erforderlich ist.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Suchen Sie im Code wird den Aufruf von <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Legen Sie`PublicKeyToken` auf den Wert an, die Sie zuvor abgerufen.  
  
12. Speichern Sie die Datei entweder als `Form1.cs` oder `Form1.vb`.  
  
13. Kompilieren Sie ihn in eine ausführbare Datei mit dem folgenden Befehl aus.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Markieren von Assemblys als optional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Um Assemblys in der ClickOnce-Anwendung als optional zu markieren, indem Sie MageUI.exe  
  
1.  Erstellen Sie unter Verwendung von MageUI.exe ein Anwendungsmanifest, wie in beschrieben [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Anwendungsmanifest aus:  
  
    -   Nennen Sie das Anwendungsmanifest `ClickOnceOnDemand`.  
  
    -   Auf der **Dateien** Seite, in der Zeile ClickOnceLibrary.dll Festlegen der **Dateityp** Spalte **keine**.  
  
    -   Auf der **Dateien** Seite in der Zeile ClickOnceLibrary.dll Typ `ClickOnceLibrary.dll` in der **Gruppe** Spalte.  
  
2.  Erstellen Sie ein Bereitstellungsmanifest mit MageUI.exe, wie in beschrieben [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Bereitstellungsmanifest aus:  
  
    -   Nennen Sie das Bereitstellungsmanifest `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testen der neuen Assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>So testen Sie die bedarfsabhängige Assembly  
  
1.  Hochladen der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung auf einem Webserver.  
  
2.  Starten Sie die Anwendung bereitgestellt, mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] über einen Webbrowser, indem Sie die URL eingeben, um das Bereitstellungsmanifest. Beim Aufrufen der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung `ClickOnceOnDemand`, und Sie sie in das Stammverzeichnis von "adatum.com" hochladen, die URL sieht dann wie folgt:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Wenn das Hauptformular angezeigt wird, drücken Sie die <xref:System.Windows.Forms.Button>. Eine Zeichenfolge in einem Meldungsfenster sollte angezeigt werden, die "Hello, World!" gelesen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>
---
title: 'Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55dfa9a360d33a73b6298f186d12810f8510b1fc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063555"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig alle Assemblys enthalten, in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung werden heruntergeladen, wenn die Anwendung zuerst ausgeführt wird. Allerdings müssen Sie Teile Ihrer Anwendung möglicherweise, die durch eine kleine Gruppe von Benutzern verwendet werden. In diesem Fall soll eine Assembly erst heruntergeladen werden, wenn eine der in ihr definierten Typen erstellt wird. Die folgende exemplarische Vorgehensweise bietet Hinweise zum Markieren bestimmter Assemblys in der Anwendung als „optional“ sowie zum Herunterladen dieser Assemblys, indem Sie Klassen im <xref:System.Deployment.Application>-Namespace verwenden, wenn diese von der Common Language Runtime (CLR) angefordert werden.  
  
> [!NOTE]
>  Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Sie benötigen eine der folgenden Komponenten in dieser exemplarischen Vorgehensweise benötigt:  
  
- Das Windows SDK. Das Windows SDK kann aus dem Microsoft Download Center heruntergeladen werden.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Zum Erstellen eines Projekts, das eine bedarfsabhängige Assembly verwendet.  
  
1. Erstellen Sie ein Verzeichnis namens ClickOnceOnDemand.  
  
2. Öffnen Sie das Windows SDK-Eingabeaufforderung oder die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Eingabeaufforderung.  
  
3. Wechseln Sie zum Verzeichnis ClickOnceOnDemand.  
  
4. Generieren Sie ein öffentliches/privates Schlüsselpaar mit dem folgenden Befehl ein:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Verwenden Sie Editor oder einem anderen Text-Editor, definieren Sie eine Klasse, die mit dem Namen `DynamicClass` mit einer einzelnen Eigenschaft mit dem Namen `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Speichern Sie den Text als eine Datei namens `ClickOnceLibrary.cs` oder `ClickOnceLibrary.vb`, abhängig von der Sprache, die Sie verwenden, zu dem Verzeichnis ClickOnceOnDemand.  
  
7. Kompilieren Sie die Datei in eine Assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Um den öffentlichen Schlüssel für die Assembly Sicherheitstoken abzurufen, verwenden Sie den folgenden Befehl aus:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Erstellen Sie eine neue Datei mit Ihren Text-Editor, und geben Sie den folgenden Code. Dieser Code erstellt eine Windows Forms-Anwendung, die die ClickOnceLibrary Assembly heruntergeladen wird, wenn dies erforderlich ist.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. Suchen Sie im Code den Aufruf von <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Legen Sie`PublicKeyToken` auf den Wert an, die Sie zuvor abgerufen haben.  
  
12. Speichern Sie die Datei entweder als `Form1.cs` oder `Form1.vb`.  
  
13. Kompilieren Sie ihn in eine ausführbare Datei mit dem folgenden Befehl aus.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Markieren von Assemblys als optional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>So markieren Assemblys als optional klicken Sie in der ClickOnce-Anwendung mit MageUI.exe  
  
1. Erstellen Sie ein Anwendungsmanifest unter Verwendung von MageUI.exe, siehe [Exemplarische Vorgehensweise: Manually Deploying a ClickOnce Application (Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung)](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Anwendungsmanifest:  
  
    - Nennen Sie das Anwendungsmanifest `ClickOnceOnDemand`.  
  
    - Auf der **Dateien** legen Sie die Seite in der Zeile ClickOnceLibrary.dll der **Dateityp** Spalte **keine**.  
  
    - Auf der **Dateien** Seite in der Zeile ClickOnceLibrary.dll Typ `ClickOnceLibrary.dll` in die **Gruppe** Spalte.  
  
2. Erstellen Sie ein Bereitstellungsmanifest mithilfe MageUI.exe, wie im [Exemplarische Vorgehensweise: Manually Deploying a ClickOnce Application (Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung)](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Verwenden Sie die folgenden Einstellungen für das Bereitstellungsmanifest aus:  
  
    - Nennen Sie das Bereitstellungsmanifest `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testen der neuen Assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>So testen Sie die bedarfsabhängige Assembly  
  
1. Hochladen Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung auf einem Webserver.  
  
2. Starten Sie die Anwendung mit bereitgestellten [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] über einen Webbrowser durch Eingeben der URL auf das Bereitstellungsmanifest. Wenn Sie aufrufen Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung `ClickOnceOnDemand`, und Sie sie in das Stammverzeichnis von "adatum.com" hochladen, die URL sieht wie folgt:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Wenn das Hauptformular angezeigt wird, drücken Sie die <xref:System.Windows.Forms.Button>. Daraufhin sollte eine Zeichenfolge in einem Meldungsfeldfenster angezeigt werden, die „Hello, World!“ lautet.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>

---
title: "Migration von Legacy-Language-Dienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services, migrieren"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Migration von Legacy-Language-Dienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können einen Dienst ältere Sprache auf eine neuere Version von Visual Studio migrieren, durch Aktualisieren des Projekts und Hinzufügen der source.extension.vsixmanifest\-Datei zum Projekt. Der Sprachdienst selbst wird weiterhin wie zuvor funktionieren, da der Visual Studio\-Editor passt.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren eines Sprachdiensts finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Migrieren Sie eine Visual Studio 2008 Language Service\-Lösung auf eine höhere Version  
 Die folgenden Schritte zeigen, wie ein Visual Studio 2008\-Beispiel mit dem Namen RegExLanguageService angepasst wird. Sie finden dieses Beispiel in einer Installation von Visual Studio 2008 SDK in die *Visual Studio SDK\-Installationspfad*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\\-Ordner.  
  
> [!IMPORTANT]
>  Wenn Ihre Sprachdienst keine Farben definiert wird, müssen Sie explizit festlegen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> zu `true` auf das VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### Migrieren Sie eine Visual Studio 2008\-Sprachdienst auf eine höhere version  
  
1.  Installieren Sie die neueren Versionen von Visual Studio und Visual Studio SDK. Weitere Informationen zum Installieren des SDK finden Sie unter [Das Visual Studio SDK installieren](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Bearbeiten Sie die RegExLangServ.csproj\-Datei \(ohne die in Visual Studio laden.  
  
     In der `Import` Knoten, die auf die Datei Microsoft.VsSDK.targets, ersetzen Sie den Wert mit dem folgenden Text.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Speichern Sie die Datei, und schließen Sie sie.  
  
4.  Öffnen Sie die Projektmappe RegExLangServ.sln.  
  
5.  Die **unidirektionales Upgrade** Fenster wird angezeigt. Klicken Sie auf **OK**.  
  
6.  Aktualisieren Sie die Projekteigenschaften. Öffnen Sie die **Projekteigenschaften** Fensters den Projektknoten in der **Projektmappen\-Explorer**, mit der rechten Maustaste, und wählen **Eigenschaften**.  
  
    -   Auf die **Anwendung** ändern **Zielframework** auf **4.6.1**.  
  
    -   Auf der **Debuggen** Registerkarte der **externes Programm starten** geben **\< Visual Studio\-Installationspfad \> \\Common7\\IDE\\devenv.exe.**.  
  
         In der **Befehlszeilenargumente** geben \/**Rootsuffix Exp**.  
  
7.  Aktualisieren Sie die folgenden Verweise:  
  
    -   Entfernen Sie den Verweis auf Microsoft.VisualStudio.Shell.9.0.dll, und fügen Sie Verweise auf Microsoft.VisualStudio.Shell.14.0.dll und Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Entfernen Sie den Verweis auf Microsoft.VisualStudio.Package.LanguageService.9.0.dll und fügen Sie einen Verweis auf Microsoft.VisualStudio.Package.LanguageService.14.0.dll hinzu.  
  
    -   Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.10.0.dll hinzu.  
  
8.  Öffnen Sie die Datei VsPkg.cs, und ändern Sie den Wert, der die `DefaultRegistryRoot` \-Attribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Das ursprüngliche Beispiel erfasst nicht die Sprachdienst, deshalb müssen Sie das folgende Attribut VsPkg.cs hinzufügen.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Sie müssen eine Datei "Source.Extension.vsixmanifest" hinzufügen.  
  
    -   Kopieren Sie diese Datei aus einer vorhandenen Erweiterung zum Projektverzeichnis. \(Eine Möglichkeit, diese Datei ist die Erstellung ein VSIX\-Projekts \(unter **Datei**, klicken Sie auf **Neu**, klicken Sie dann auf **Projekt**. Klicken Sie unter Visual Basic oder c\# auf **Erweiterbarkeit**, und wählen Sie dann **VSIX\-Projekt**.\)  
  
    -   Die Datei dem Projekt hinzufügen.  
  
    -   In der Datei **Eigenschaften**, legen **Buildvorgang** auf **keine**.  
  
    -   Öffnen Sie die Datei mit den **VSIX\-Manifest\-Editor**.  
  
    -   Ändern Sie die folgenden Felder:  
  
    -   **ID**: RegExLangServ  
  
    -   **Produktname**: RegExLangServ  
  
    -   **Beschreibung**: eine Sprachdienst regulären Ausdruck.  
  
    -   Unter **Bestand**, klicken Sie auf **Neu**, wählen die **Typ** auf **Microsoft.VisualStudio.VsPackage**, legen die **Quelle** auf **ein Projekt in der aktuellen Projektmappe**, und legen Sie dann die **Projekt** auf **RegExLangServ**.  
  
    -   Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projektmappe. Die erstellten Dateien werden bereitgestellt, um **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**.  
  
12. Beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio geöffnet.  
  
## Siehe auch  
 [Ältere Sprache Service\-Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md)
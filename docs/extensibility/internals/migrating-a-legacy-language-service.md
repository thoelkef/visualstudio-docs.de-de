---
title: Migrieren von einem Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135849"
---
# <a name="migrating-a-legacy-language-service"></a>Migrieren von einem Legacy-Sprachdienst
Sie können einen legacy-Sprachdienst auf eine höhere Version von Visual Studio migrieren, durch Aktualisieren des Projekts und Hinzufügen einer Datei "Source.Extension.vsixmanifest" zum Projekt. Der Sprachdienst selbst werden wie zuvor funktionieren weiterhin, weil der Visual Studio-Editor passt.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrieren Sie eine Visual Studio 2008 Language Service-Projektmappe auf eine höhere Version  
 Die folgenden Schritte zeigen, wie ein Visual Studio 2008-Beispiel, das mit dem Namen RegExLanguageService angepasst werden kann. Sie finden dieses Beispiel in einer Visual Studio 2008 SDK-Installation in der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ Ordner.  
  
> [!IMPORTANT]
>  Wenn Ihre Sprachdienst Farben nicht definiert ist, müssen Sie explizit festlegen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> zu `true` für das VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Migrieren Sie einen Visual Studio 2008-Sprachdienst auf eine höhere version  
  
1.  Installieren Sie die neueren Versionen von Visual Studio und Visual Studio SDK. Weitere Informationen zu Möglichkeiten, das SDK zu installieren, finden Sie unter [Installieren von Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Bearbeiten Sie die RegExLangServ.csproj-Datei (ohne Laden in Visual Studio.  
  
     In der `Import` Knoten, der auf die Datei Microsoft.VsSDK.targets verweist ersetzen Sie den Wert mit dem folgenden Text.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Speichern Sie die Datei, und schließen sie dann.  
  
4.  Öffnen Sie die Projektmappe RegExLangServ.sln.  
  
5.  Die **unidirektionales Upgrade** Fenster wird angezeigt. Klicken Sie auf **OK**.  
  
6.  Aktualisieren Sie die Projekteigenschaften an. Öffnen der **Projekteigenschaften** dazu den Projektknoten im Fenster der **Projektmappen-Explorer**, mit der rechten Maustaste und auswählen **Eigenschaften**.  
  
    -   Auf der **Anwendung** Registerkarte **Zielframework** auf **4.6.1**.  
  
    -   Auf der **Debuggen** Registerkarte die **externes Programm starten** geben  **\<Visual Studio-Installationspfad > \Common7\IDE\devenv.exe.**.  
  
         In der **Befehlszeilenargumente** geben /**Rootsuffix Exp**.  
  
7.  Aktualisieren Sie die folgenden Verweise:  
  
    -   Entfernen Sie den Verweis auf Microsoft.VisualStudio.Shell.9.0.dll, und fügen Sie Verweise auf Microsoft.VisualStudio.Shell.14.0.dll und Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Entfernen Sie den Verweis auf Microsoft.VisualStudio.Package.LanguageService.9.0.dll, und fügen Sie einen Verweis auf Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Öffnen Sie die Datei VsPkg.cs und ändern Sie den Wert, der die `DefaultRegistryRoot` -Attribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Der Sprachdienst wird in der ursprünglichen Stichprobe nicht registriert, damit Sie das folgende Attribut VsPkg.cs hinzufügen müssen.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Sie müssen eine Datei "Source.Extension.vsixmanifest" hinzufügen.  
  
    -   Kopieren Sie diese Datei aus einer vorhandenen Erweiterung zum Projektverzeichnis an. (Eine Möglichkeit, diese Datei wird zum Erstellen eines VSIX-Projekts (unter **Datei**, klicken Sie auf **neu**, klicken Sie dann auf **Projekt**. Unter Visual Basic oder c# auf **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekts**.)  
  
    -   Die Datei dem Projekt hinzufügen.  
  
    -   In der Datei **Eigenschaften**legen **Buildvorgang** auf **keine**.  
  
    -   Öffnen Sie die Datei mit den **VSIX-Manifest-Editor**.  
  
    -   Ändern Sie die folgenden Felder:  
  
    -   **ID**: RegExLangServ  
  
    -   **Produktname**: RegExLangServ  
  
    -   **Beschreibung**: einen regulären Ausdruck Sprachdienst.  
  
    -   Unter **Bestand**, klicken Sie auf **neu**, wählen die **Typ** auf **Microsoft.VisualStudio.VsPackage**legen die **Quelle** auf **ein Projekt in der aktuellen Projektmappe**, und legen Sie dann die **Projekt** auf **RegExLangServ**.  
  
    -   Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projektmappe. Die erstellten Dateien werden bereitgestellt, um **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio geöffnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)
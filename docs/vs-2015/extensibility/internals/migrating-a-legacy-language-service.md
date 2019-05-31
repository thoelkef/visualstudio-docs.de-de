---
title: Migrieren eines Legacysprachdiensts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6c5d665367f2d5af9e2dd6d2a7d664e50f4830
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434374"
---
# <a name="migrating-a-legacy-language-service"></a>Migrieren eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können eine legacysprachdiensten auf eine neuere Version von Visual Studio migrieren, durch Aktualisieren des Projekts und dem Projekt eine Datei "Source.Extension.vsixmanifest" hinzugefügt. Der Sprachdienst selbst werden wie zuvor funktionieren weiterhin, weil Visual Studio-Editor passt.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrieren Sie eine Visual Studio 2008 Language Service-Lösung auf eine höhere Version  
 Die folgenden Schritte zeigen, wie Sie eine Visual Studio 2008-Beispiel, das mit dem Namen RegExLanguageService anpassen. Sie finden dieses Beispiel in einer Visual Studio 2008 SDK-Installation in der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\-Ordner.  
  
> [!IMPORTANT]
> Wenn es sich bei der Sprachdienst Farben nicht definiert, müssen Sie explizit festlegen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> zu `true` für das VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Einen Visual Studio 2008-Sprachdienst auf eine neuere Version migrieren.  
  
1. Installieren Sie die neueren Versionen von Visual Studio und Visual Studio SDK. Weitere Informationen zu Möglichkeiten, um das SDK zu installieren, finden Sie unter [Installieren von Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2. Bearbeiten Sie die RegExLangServ.csproj-Datei (ohne Laden in Visual Studio.  
  
     In der `Import` Knoten, der auf die Datei Microsoft.VsSDK.targets verweist ersetzen Sie den Wert mit dem folgenden Text.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3. Speichern Sie die Datei, und schließen Sie sie.  
  
4. Öffnen Sie die RegExLangServ.sln-Projektmappe.  
  
5. Die **unidirektionales Upgrade** Fenster wird angezeigt. Klicken Sie auf **OK**.  
  
6. Aktualisieren Sie die Projekteigenschaften an. Öffnen der **Projekteigenschaften** Fenster, indem Sie den Projektknoten im Auswählen der **Projektmappen-Explorer**, mit der rechten Maustaste, und wählen **Eigenschaften**.  
  
    - Auf der **Anwendung** Registerkarte **Zielframework** zu **4.6.1**.  
  
    - Auf der **Debuggen** Registerkarte die **externes Programm starten** geben  **\<Visual Studio-Installationspfad > \Common7\IDE\devenv.exe.** .  
  
         In der **Befehlszeilenargumente** geben /**Rootsuffix Exp**.  
  
7. Aktualisieren Sie die folgenden Verweise:  
  
    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Shell.9.0.dll, und fügen Sie Verweise auf Microsoft.VisualStudio.Shell.14.0.dll und Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Package.LanguageService.9.0.dll, und fügen Sie einen Verweis auf Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    - Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.10.0.dll hinzu.  
  
8. Öffnen Sie die Datei VsPkg.cs und ändern Sie den Wert, der die `DefaultRegistryRoot` Attribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Das ursprüngliche Beispiel werden der Sprachdienst nicht registriert, sodass Sie das folgende Attribut VsPkg.cs hinzufügen müssen.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Sie müssen eine Datei "Source.Extension.vsixmanifest" hinzufügen.  
  
    - Kopieren Sie diese Datei aus einer vorhandenen Erweiterung zu Ihrem Projektverzeichnis. (Eine Möglichkeit zum Abrufen dieser Datei wird zum Erstellen eines VSIX-Projekts (unter **Datei**, klicken Sie auf **neu**, klicken Sie dann auf **Projekt**. Klicken Sie in Visual Basic oder c# auf **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**.)  
  
    - Die Datei zu Ihrem Projekt hinzufügen.  
  
    - In der Datei **Eigenschaften**legen **Buildvorgang** zu **keine**.  
  
    - Öffnen Sie die Datei mit den **VSIX-Manifest-Editor**.  
  
    - Ändern Sie die folgenden Felder:  
  
    - **ID**: RegExLangServ  
  
    - **Produktname**: RegExLangServ  
  
    - **Beschreibung:** Sprachdienst für einen regulären Ausdruck.  
  
    - Unter **Assets**, klicken Sie auf **neu**, wählen die **Typ** zu **"Microsoft.VisualStudio.VSPackage"** legen die **Quelle** zu **ein Projekt in der aktuellen Projektmappe**, und legen Sie dann die **Projekt** zu **RegExLangServ**.  
  
    - Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projektmappe. Die erstellten Dateien bereitgestellt werden, um **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\** .  
  
12. Beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio geöffnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)

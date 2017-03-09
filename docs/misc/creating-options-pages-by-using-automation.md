---
title: "Erstellen von Optionsseiten mithilfe der Automatisierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Optionsseiten (Tools) [Visual Studio SDK], erstellen"
  - "Automatisierung [Visual Studio SDK], Erstellen von Optionsseiten (Tools)"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Erstellen von Optionsseiten mithilfe der Automatisierung
Verwaltetes VSPackages Automatisierung kann verwendet werden, um die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) indem er **Optionen** Seiten auf den **Extras** Menü erweitert werden soll.  
  
 Eine **Extras\/Optionen** Seite handelt es sich im Grunde um ein Benutzersteuerelement und wird auf die gleiche Weise wie jedes andere Steuerelement codiert.  Normalerweise würden Sie einen des vom Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE verwenden, um das Objekt zu erstellen und Benutzersteuerelemente hinzufügen.  
  
> [!NOTE]
>  **Extras\/Optionen** Seiten, die als Dialogfeld unter Verwendung `DialogProc` implementiert werden, um Fenstermeldungen zu bearbeiten, müssen nicht modale Dialogfelder sein und dürfen die `EndDialog`\-Funktion nicht aufrufen.  
  
 Sie sollten das Automatisierungsobjekt, das ein VSPackage Umgebungen zu unterstützen benutzersteuerelement Eigenschaften bereitstellt.  
  
## Automatisierungs\-Unterstützung für die Optionsseiten im Menü Extras implementiert den Interop\-Assemblys  
 Um das Automatisierungsmodell zu unterstützen, muss ein VSPackage ein Automatisierungsobjekt erstellen und registrieren.  Weitere Informationen finden Sie unter [Automatisierte für VSPackages](../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Wenn Code, der das Automatisierungsmodells `DTE.Properties` für die Eigenschaftenauflistung einer angegebenen **Extras\/Optionen** Seite aufruft, wird die IDE das Automatisierungsobjekt, das von der Implementierung von VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> bereitgestellt wird, um die Auflistung und zurückzugeben <xref:EnvDTE.Property> Zugriff auf die konstituierenden Objekte zu ermöglichen.  
  
 **Hinweis** das Automatisierungsobjekt, das von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> zurückgegeben wird, hängt vom angegebenen GUID ab \(bei einem VSPackage mehr als ein Automatisierungsobjekt unterstützt\).  Weitere Informationen über das Implementieren von Automatisierungsobjekten finden Sie unter [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../extensibility/internals/automation-support-for-options-pages.md).  
  
 Eine **Extras\/Optionen** Seite besteht aus zwei Bezeichnern angegeben.  Der erste Bezeichner ist eine Zeichenfolge, die den Ordner angibt, der das Element im **Optionen**\-Abschnitt des **Extras** Menüelemente enthält.  Der zweite Bezeichner ist eine Zeichenfolge, die das jeweilige Element im Ordner angibt.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md).  
  
 Zwei Registrierungseinträge sind erforderlich, um ein Automatisierungsobjekt zu registrieren:  
  
-   Klicken Sie unter HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version* \\Packages\\*\<PackageGUID\>*\\ Automatisierung  
  
-   Klicken Sie unter HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ *\<Version\>* \\ AutomationProperties  
  
     Dabei  *\<Version\>*  die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist \(z. B. 8.0\), und die GUID ist  *\<PackageGUID\>*  VSPackages, das das Automatisierungsobjekt implementiert.  
  
 Abhängig von der Konfiguration AutomationProperties\-Registrierungseintrag, unter dem der Zustand einer **Extras\/Optionen** Seite wird automatisch durch den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Mechanismus zur Einstellungen gespeichert und wiederhergestellt, wenn ein Benutzer den **Einstellungen importieren und exportieren** Befehl für das **Extras** Menü ausgewählt wird.  Weitere Informationen zum Speichern von **Extras\/Optionen** Seiteneinstellungen finden Sie unter [Registrieren benutzerdefinierter Seiten für Optionen](../misc/registering-custom-options-pages.md).  
  
 Eine Anwendung das Automatisierungsmodell nicht verwendet werden, um Unterstützung für Eigenschaften und Einstellungen einer **Extras\/Optionen** Seite zu implementieren.  
  
 Dies kann aus mehreren Gründen geeignet:  
  
-   Die Einstellungen, die von der **Extras\/Optionen** Seite behandelt werden, sind in der Struktur als komplexer, was das relativ flachen Automatisierungseigenschaften Modell unterstützt.  
  
-   Es gibt eine Anforderung an andere Anwendungen, die **Extras\/Optionen** Seite programmgesteuert verwalten zu verhindern.  
  
-   Besondere Zugreifen auf Steuerelemente oder Sicherheitsfunktionen sind erforderlich.  
  
 In diesen Fällen kann **Extras\/Optionen** VSPackages Unterstützung vonseiten auf irgendeine Weise implementieren, die geeignet ist.  Allerdings müssen sie:  
  
-   Behandeln Sie die Einstellung von **Extras\/Optionen** Seiteneigenschaften.  
  
-   Verwalten von Dauerhaftigkeit von **Extras\/Optionen** Seitenzustand von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen.  
  
-   Erstellen Sie eine API bereit, wenn Sie gewünscht sein, damit andere Anwendungen die **Extras\/Optionen** Seite verwenden.  
  
 Die Eigenschaften des **Schriftarten und Farben** Dialogfelds ist ein Beispiel für eine **Extras\/Optionen** Seite, die nicht vom Automatisierungsmodell geändert werden kann.  Stattdessen wird ein separates API auf Grundlage der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>\-Schnittstelle bereitgestellt, um die programmgesteuerte Bearbeitung der Seite **Schriftarten und FarbenExtras\/Optionen** zu ermöglichen.  Weitere Informationen zum Steuern der Seite **Schriftarten und FarbenExtras\/Optionen** finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
## Automatisierungs\-Unterstützung für Optionsseiten im Menü Extras im verwalteten Paketframeworks  
 Legen Sie die Eigenschaft <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> registrierender <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>\-Instanz einer Implementierung fest, um anzugeben, dass eine verwaltete Implementierung einer **Extras\/Optionen** Seite Paket Framework\-Basis Automatisierung unterstützt.  
  
 **Extras\/Optionen** Seiten, die von <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleitet sind, werden mit einem Automatisierungsobjekt angegeben, das überschrieben werden kann.  
  
 Wenn eine Seite **Extras\/Optionen** Implementierung der Automatisierung nicht unterstützt, muss die Implementierung über eine eigene API angeben, um den programmgesteuerten Zugriff auf die **Extras\/Optionen** Seite zu ermöglichen.  
  
> [!NOTE]
>  Die **Schriftarten und Farben** Seite der IDE ist ein Beispiel für eine **Extras\/Optionen** Seite, die keine Automatisierung unterstützt, doch bietet Zugriff auf die **Extras\/Optionen** Seite durch seinen eigenen API.  Weitere Informationen finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
## Siehe auch  
 [Erweitern der Visual Studio\-Umgebung](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Erstellen von Optionsseiten mithilfe von Interop\-Assemblys](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Optionen \(Seiten\) erstellen](../extensibility/internals/creating-options-pages.md)   
 [Gewusst wie: Erstellen benutzerdefinierter Optionsseiten](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../extensibility/internals/automation-support-for-options-pages.md)   
 [Verwenden von Optionsseiten](../misc/using-options-pages.md)
---
title: "Optionen und Optionen (Seiten) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unterstützung für Optionen Seiten [Visual Studio SDK] verwaltet Paket Framework-Tools"
  - "verwaltete Paketframework, Seiten-Support Tools-Optionen"
  - "Unterstützung von Tools-Optionen (Seiten)"
  - "Optionen (Seiten) [Visual Studio SDK] Layouts-Tools"
  - "Optionen (Seiten) [Visual Studio SDK] Attribute-Tools"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# Optionen und Optionen (Seiten)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auf **Optionen** auf der **Tools** Menü geöffnet wird die **Optionen** \(Dialogfeld\). Die Optionen in diesem Dialogfeld werden zusammen als Optionen \(Seiten\) bezeichnet. Die Strukturansicht im Navigationsbereich Optionen Kategorien und jede Kategorie Optionen \(Seiten\). Wenn Sie eine Seite auswählen, werden die Optionen im rechten Bereich angezeigt. Diese Seiten können Sie die Werte der Optionen zu ändern, die den Status von VSPackages zu bestimmen.  
  
## Unterstützung für Optionen \(Seiten\)  
 Die <xref:Microsoft.VisualStudio.Shell.Package> \-Klasse bietet Unterstützung für das Erstellen von Optionsseiten und Optionen Kategorien. Die <xref:Microsoft.VisualStudio.Shell.DialogPage> \-Klasse implementiert eine Optionsseite.  
  
 Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> bietet die öffentlichen Eigenschaften für einem Benutzer in einem generischen Raster von Eigenschaften. Sie können dieses Verhalten anpassen, indem Sie auf der Seite, um eine benutzerdefinierte Seite erstellen, die eine eigene Benutzeroberfläche \(UI\) verfügt über verschiedene Methoden überschreiben. Weitere Informationen finden Sie unter [Erstellen eine Optionsseite](../../extensibility/creating-an-options-page.md).  
  
 Die <xref:Microsoft.VisualStudio.Shell.DialogPage> \-Klasse implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager>, stellt Dauerhaftigkeit für Optionsseiten und benutzereinstellungen. Die standardimplementierungen der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> und <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> Methoden werden die eigenschaftenänderungen in einer Benutzerabschnitt der Registrierung beibehalten, wenn die Eigenschaft in und aus einer Zeichenfolge konvertiert werden kann.  
  
## Optionen\-Seite Registrierungspfad  
 Standardmäßig richtet sich der Registrierungspfad der Eigenschaften einer Optionsseite verwaltet durch Kombination von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, das Wort DialogPage und des Typnamens der Seitenklasse Optionen. Beispielsweise kann eine Seitenklasse Optionen wie folgt definiert werden.  
  
 [!code-cs[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> ist HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, und klicken Sie dann die Name\-Wert\-Paare Unterschlüssel des HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral sind.  
  
 Der Registrierungspfad der Optionsseite selbst wird bestimmt durch Kombination von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, das Wort ToolsOptionsPages und die Optionen auf der Seite Kategorie und Name. Beispielsweise verfügt die benutzerdefinierte Optionsseite die Kategorie eigene Optionsseiten, und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> ist HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, und klicken Sie dann die Optionsseite den Registrierungsschlüssel HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My Option Pages\\Custom hat.  
  
## Extras\/Optionen Seitenattribute und Layout  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut bestimmt die Gruppierung von benutzerdefinierter Optionsseiten Kategorien in der Navigationsstruktur des der **Optionen** \(Dialogfeld\). Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ordnet eine Optionsseite des VSPackage, die die Schnittstelle bereitstellt. Betrachten Sie das folgende Codefragment:  
  
 [!code-cs[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Dies wird deklariert, dass MyPackage zwei Optionsseiten, OptionsPageGeneral und OptionsPageCustom bietet. In der **Optionen** Dialogfeld beide Optionen \(Seiten\) angezeigt, der **Eigene Optionsseiten** Kategorie als **Allgemeine** und **benutzerdefinierte**, bzw..  
  
## Optionsattribute und Layout  
 Die Benutzeroberfläche \(UI\) die Seite bestimmt die Darstellung der Optionen in einem benutzerdefinierten Optionen. Layout, Beschriftung und Beschreibung der Optionen in einem generischen Optionen werden durch die folgenden Attribute bestimmt:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Bestimmt die Kategorie der Option.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Bestimmt den Anzeigenamen der Option.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Bestimmt die Beschreibung der Option.  
  
    > [!NOTE]
    >  Entsprechende Attribute, SRCategory, LocDisplayName und SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und werden in definiert die [verwaltetes projektbeispiel](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-cs[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 Die OptionInteger\-Option wird angezeigt, auf der Optionsseite als **Integer\-Option** in der **Meine Optionen** Kategorie. Wenn die Option ausgewählt ist, die Beschreibung der **Meine Integer\-Option**, wird im Beschreibungsfeld angezeigt.  
  
## Zugreifen auf Optionsseiten aus einem anderen VSPackage  
 Ein VSPackage, das gehostet und verwaltet eine Optionsseite kann aus einem anderen VSPackage programmgesteuert zugegriffen werden, mithilfe des Automatisierungsmodells. Beispielsweise wird im folgenden Code ein VSPackage registriert, als Host für eine Seite.  
  
 [!code-cs[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Das folgende Codefragment ruft den Wert der OptionInteger MyOptionPage:  
  
 [!code-cs[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut registriert eine Optionsseite, unter der AutomationProperties\-Taste, wenn die Seite registriert ist die `SupportsAutomation` Argument des Attributs ist `true`. Automatisierung untersucht dieses Registrierungseintrags, um die zugehörigen VSPackage und die Automatisierung zu suchen, und klicken Sie dann greift auf die Eigenschaft über der gehosteten Optionsseite in diesem Fall eigene Rasterseite.  
  
 Der Registrierungspfad der Benutzeroberflächenautomatisierungs\-Eigenschaft wird bestimmt durch Kombination von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, das Wort AutomationProperties und die Optionen auf der Seite Kategorie und Name. Beispielsweise verfügt die Optionsseite die eigene Kategorie, den Namen My Rasterseite und <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, und klicken Sie dann auf die Benutzeroberflächenautomatisierungs\-Eigenschaft hat den Registrierungsschlüssel HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My Kategorie\\Eigener Rasterseite.  
  
> [!NOTE]
>  Der kanonische Name, meine Category.My Rasterseite, ist der Wert des Unterschlüssels Name des Schlüssels.
---
title: Optionen und Optionsseiten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73eb5ab6c139d4ce6bdfb8a5a310ca447ce4267c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872121"
---
# <a name="options-and-options-pages"></a>Optionen und Optionsseiten
Auf **Optionen** auf die **Tools** Menü geöffnet wird die **Optionen** Dialogfeld. Die Optionen in diesem Dialogfeld werden zusammen als Optionsseiten bezeichnet. Das Struktursteuerelement im Navigationsbereich gehören Optionen, und jede Kategorie verfügt über Optionen-Seiten. Wenn Sie eine Seite auswählen, werden die Optionen im rechten Bereich angezeigt. Diese Seiten können Sie die Werte der Optionen zu ändern, die den Status eines VSPackage zu bestimmen.  
  
## <a name="support-for-options-pages"></a>Unterstützung für Optionsseiten  
 Die <xref:Microsoft.VisualStudio.Shell.Package> -Klasse bietet Unterstützung für das Erstellen von Optionsseiten und Optionen Kategorien. Die <xref:Microsoft.VisualStudio.Shell.DialogPage> -Klasse implementiert eine Seite mit Optionen.  
  
 Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> bietet die öffentlichen Eigenschaften zu einem Benutzer in einem generischen Raster von Eigenschaften. Sie können dieses Verhalten durch Überschreiben der verschiedenen Methoden auf der Seite zum Erstellen einer benutzerdefinierten Optionen-Seite, die eine eigene Benutzeroberfläche (UI) anpassen. Weitere Informationen finden Sie unter [Erstellen einer Optionsseite](../../extensibility/creating-an-options-page.md).  
  
 Die <xref:Microsoft.VisualStudio.Shell.DialogPage> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager>, bietet Sie die Persistenz für Optionsseiten und benutzereinstellungen. Die standardimplementierungen der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> und <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> Methoden eigenschaftenänderungen in einem Abschnitt der Registrierung beizubehalten, wenn die Eigenschaft in und aus einer Zeichenfolge konvertiert werden kann.  
  
## <a name="options-page-registry-path"></a>Optionen-Seite-Registrierungspfad  
 Standardmäßig richtet sich der Registrierungspfad der die Eigenschaften, die von einer Optionsseite verwaltet durch Kombinieren von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, das Wort DialogPage und der Typname der Optionen für Page-Klasse. Eine Optionsklasse für die Seite kann beispielsweise wie folgt definiert werden.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, ist, dann sind die Namen und Wert-Paare Unterschlüssel des HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Der Registrierungspfad der Optionsseite selbst richtet sich nach der Kombination von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, das Wort, ToolsOptionsPages und die Optionen-Seite Eigenschaftenkategorien und-Namen. Beispielsweise verfügt die benutzerdefinierte Optionen-Seite die Kategorie, meine Optionsseiten, und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, ist, dann hat die Seite "Optionen" den Schlüssel "hkey_local_machine\software\microsoft\" VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Seitenattributen Extras/Optionen und Layout  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ermittelt die Gruppierung von benutzerdefinierter Seiten für Optionen in der Navigationsstruktur des in Kategorien der **Optionen** Dialogfeld. Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ordnet eine Seite mit Optionen, mit dem VSPackage, das die Schnittstelle bereitstellt. Betrachten Sie das folgende Codefragment:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Damit wird deklariert, dass "myPackage" zwei Optionsseiten, OptionsPageGeneral und OptionsPageCustom bereitstellt. In der **Optionen** Dialogfeld, beide Optionsseiten angezeigt, der **Meine Optionsseiten** als Kategorie **allgemeine** und **benutzerdefinierte**bzw.  
  
## <a name="option-attributes-and-layout"></a>Optionsattribute und Layout  
 Die Benutzeroberfläche (UI), die die Seite enthält bestimmt die Darstellung der Optionen in einer benutzerdefinierten Optionen. Das Layout, Bezeichnung und Beschreibung der Optionen in einer generischen Optionen werden durch die folgenden Attribute bestimmt:  
  
- <xref:System.ComponentModel.CategoryAttribute> Bestimmt die Kategorie der Option.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Bestimmt den Anzeigenamen der Option.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Bestimmt, die Beschreibung der Option.  
  
  > [!NOTE]
  >  Entsprechende Attribute, SRCategory, LocDisplayName SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und werden definiert, der [verwalteten projektbeispiel](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Betrachten Sie das folgende Codefragment:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
  Die OptionInteger-Option wird angezeigt, auf der Seite "Optionen" als **Integer-Option** in die **Meine Optionen** Kategorie. Wenn die Option ausgewählt ist, die Beschreibung und den **Meine ganze Zahl Option**, in das Beschreibungsfeld angezeigt wird.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Zugreifen auf Optionsseiten aus einem anderen VSPackage  
 Eine VSPackage, die hostet und verwaltet eine Seite mit Optionen kann programmgesteuert aus einem anderen VSPackage über das Automatisierungsmodell zugegriffen werden. Beispielsweise wird in den folgenden Code eine VSPackage registriert, als Host für eine Optionsseite.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Das folgende Codefragment ruft den Wert der OptionInteger MyOptionPage ab:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut registriert eine Seite mit Optionen, die Seite registriert ist, unter dem AutomationProperties-Taste, wenn die `SupportsAutomation` Argument des Attributs ist `true`. Automation untersucht dieses Registrierungseintrags, um die zugehörigen VSPackages und Automatisierung zu suchen, und klicken Sie dann greift auf die Eigenschaft über der gehosteten Optionsseite in diesem Fall Meine Rasterseite.  
  
 Der Registrierungspfad der Automatisierungseigenschaft wird bestimmt durch Kombinieren von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, das Wort, AutomationProperties und die Optionen-Seite Eigenschaftenkategorien und-Namen. Wenn die Seite "Optionen" My Category-Kategorie, den Namen Meine Rasterseite hat z. B. und <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, und klicken Sie dann auf die Automatisierungseigenschaft hat den Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Kategorie\Eigener der Rasterseite.  
  
> [!NOTE]
>  Der kanonische Name, meine Category.My Rasterseite, ist der Wert des Unterschlüssels Name dieses Schlüssels.
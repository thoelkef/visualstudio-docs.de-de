---
title: Optionsseiten und Optionen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 665567430ac9fdfdc301329972a3a4f7b621a241
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="options-and-options-pages"></a>Optionsseiten und Optionen
Auf **Optionen** auf die **Tools** Menü geöffnet wird die **Optionen** (Dialogfeld). Die Optionen in diesem Dialogfeld werden zusammenfassend als Optionsseiten bezeichnet. Strukturansicht-Steuerelements im Navigationsbereich enthält Optionen Kategorien, und jede Kategorie hat Optionsseiten. Wenn Sie eine Seite auswählen, werden die zugehörigen Optionen im rechten Bereich. Diese Seiten können Sie die Werte der Optionen ändern, die den Status eines VSPackage zu bestimmen.  
  
## <a name="support-for-options-pages"></a>Unterstützung für Optionsseiten  
 Die <xref:Microsoft.VisualStudio.Shell.Package> Klasse bietet Unterstützung zum Erstellen von Optionsseiten und Optionen Kategorien. Die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse implementiert, die eine Seite "Optionen".  
  
 Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> bietet die öffentlichen Eigenschaften für einem Benutzer in einem generischen Raster von Eigenschaften. Sie können dieses Verhalten anpassen, indem Sie auf der Seite um eine benutzerdefinierte Optionsseite zu erstellen, die eine eigene Benutzeroberfläche (UI) verfügt über verschiedene Methoden überschreiben. Weitere Informationen finden Sie unter [Erstellen einer Optionsseite](../../extensibility/creating-an-options-page.md).  
  
 Die <xref:Microsoft.VisualStudio.Shell.DialogPage> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager>, stellt Persistenz Optionsseiten und ebenso für benutzereinstellungen. Die standardmäßigen Implementierungen von der <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> und <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> Methoden werden die eigenschaftenänderungen in einer Benutzerabschnitt der Registrierung beibehalten, wenn die Eigenschaft in und aus einer Zeichenfolge konvertiert werden kann.  
  
## <a name="options-page-registry-path"></a>Optionen-Seite Registrierungspfad  
 Standardmäßig richtet sich der Registrierungspfad der die Eigenschaften, die von einer Optionsseite verwaltet kombinierten <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, das Wort DialogPage und der Typname der Optionen Page-Klasse. Beispielsweise könnte eine Optionsklasse für die Seite wie folgt definiert.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, ist, und klicken Sie dann die Eigenschaft Name-Wert-Paare Unterschlüssel des HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ sind Company.OptionsPage.OptionsPageGeneral.  
  
 Der Registrierungspfad der Optionsseite selbst richtet sich nach Kombination von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, Seite "das Wort, ToolsOptionsPages und die Optionen" Eigenschaftenkategorien und-Namen. Beispielsweise besitzt der benutzerdefinierten "Optionen" die Kategorie Meine Optionsseiten, und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, ist, dann hat die Seite "Optionen" den Schlüssel "hkey_local_machine\software\microsoft\" VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Die Seitenattribute Extras/Optionen und Layout  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ermittelt die Gruppierung von benutzerdefinierter Seiten für Optionen Kategorien in der Navigationsstruktur des der **Optionen** (Dialogfeld). Die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ordnet eine Seite "Optionen" das VSPackage, das die Schnittstelle bereitstellt. Betrachten Sie das folgende Codefragment:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Dies wird deklariert, dass MyPackage stellt zwei Optionsseiten, OptionsPageGeneral und OptionsPageCustom bereit. In der **Optionen** (Dialogfeld), beide Optionsseiten angezeigt, der **Meine Optionsseiten** Kategorie als **allgemeine** und **benutzerdefinierte**bzw..  
  
## <a name="option-attributes-and-layout"></a>Optionsattribute und Layout  
 Die Benutzeroberfläche (UI), die die Seite enthält bestimmt die Darstellung der Optionen in eine benutzerdefinierte Optionsseite. Layout, Bezeichnung und Beschreibung der Optionen in einem generischen Optionen werden durch die folgenden Attribute bestimmt:  
  
-   <xref:System.ComponentModel.CategoryAttribute>Bestimmt die Kategorie der Option.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>Bestimmt den Anzeigenamen der Option.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>Bestimmt die Beschreibung der Option "".  
  
    > [!NOTE]
    >  Entsprechende Attribute, SRCategory LocDisplayName und SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und werden im definiert die [verwalteten projektbeispiel](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 Die OptionInteger-Option wird angezeigt, auf der Seite "Optionen" als **Integer-Option** in der **Meine Optionen** Kategorie. Wenn die Option ausgewählt ist, die Beschreibung **Integer-Option**, wird im Beschreibungsfeld angezeigt.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Beim Zugriff auf den Optionsseiten aus einem anderen VSPackage  
 Mithilfe des Automatisierungsmodells, kann das ein VSPackage, das gehostet und verwaltet eine Optionsseite programmgesteuert aus einem anderen VSPackage zugegriffen werden. Beispielsweise wird im folgenden Code eine VSPackage registriert, als Host für eine Optionsseite.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Das folgende Codefragment ruft den Wert der OptionInteger MyOptionPage ab:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut registriert eine Optionsseite, die Seite wird registriert, unter der AutomationProperties-Taste, wenn die `SupportsAutomation` Argument des Attributs ist `true`. Automatisierung dieses Registrierungseintrags finden Sie die zugeordneten VSPackages und Automatisierung untersucht, und klicken Sie dann greift auf die Eigenschaft über der gehosteten "Optionen" in diesem Fall Meine Rasterseite.  
  
 Der Registrierungspfad der Automation-Eigenschaft wird bestimmt durch Kombinieren von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, Seite "das Wort, AutomationProperties und die Optionen" Eigenschaftenkategorien und-Namen. Angenommen, die Seite "Optionen" die eigene Kategorie, den Namen Meine Rasterseite hat und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, und klicken Sie dann auf die Automatisierungseigenschaft hat den Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Kategorie\Eigener der Rasterseite.  
  
> [!NOTE]
>  Der kanonische Name, meine Category.My Rasterseite, ist der Wert des Unterschlüssels "Name" dieses Schlüssels.
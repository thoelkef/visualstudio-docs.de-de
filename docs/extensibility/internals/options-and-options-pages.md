---
title: Optionen und Optionen Seiten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706842"
---
# <a name="options-and-options-pages"></a>Optionen und Optionsseiten
Wenn Sie im Menü **Extras** auf **Optionen** klicken, wird das Dialogfeld **Optionen** geöffnet. Die Optionen in diesem Dialogfeld werden zusammen als Optionsseiten bezeichnet. Das Struktursteuerelement im Navigationsbereich enthält Optionskategorien, und jede Kategorie verfügt über Optionsseiten. Wenn Sie eine Seite auswählen, werden die Optionen im rechten Bereich angezeigt. Auf diesen Seiten können Sie die Werte der Optionen ändern, die den Status eines VSPackage bestimmen.

## <a name="support-for-options-pages"></a>Unterstützung für Optionsseiten
 Die <xref:Microsoft.VisualStudio.Shell.Package> Klasse bietet Unterstützung für das Erstellen von Optionsseiten und Optionskategorien. Die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse implementiert eine Optionsseite.

 Die Standardimplementierung <xref:Microsoft.VisualStudio.Shell.DialogPage> von bietet seine öffentlichen Eigenschaften einem Benutzer in einem generischen Raster von Eigenschaften an. Sie können dieses Verhalten anpassen, indem Sie verschiedene Methoden auf der Seite überschreiben, um eine benutzerdefinierte Optionsseite mit einer eigenen Benutzeroberfläche (UI) zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer Optionsseite](../../extensibility/creating-an-options-page.md).

 Die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse <xref:Microsoft.VisualStudio.Shell.IProfileManager>implementiert , die Persistenz für Optionsseiten und auch für Benutzereinstellungen bereitstellt. Die Standardimplementierungen <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> der <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> und -methoden beibehalten Eigenschaftenänderungen in einem Benutzerabschnitt der Registrierung, wenn die Eigenschaft in und aus einer Zeichenfolge konvertiert werden kann.

## <a name="options-page-registry-path"></a>Optionen Seite Registrierungspfad
 Standardmäßig wird der Registrierungspfad der Eigenschaften, die von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>einer Optionsseite verwaltet werden, durch Kombinieren des Worts DialogPage und des Typnamens der Optionsseitenklasse bestimmt. Eine Optionsseitenklasse kann z. B. wie folgt definiert werden.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Wenn <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> es sich um HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0Exp handelt, sind die Eigenschaftsnamen- und Wertpaare Unterschlüssel von HKEY_CURRENT_USER-Software,Microsoft-VisualStudio-8.0Exp-DialogPage-Unternehmen.OptionsPage.OptionsPageGeneral.

 Der Registrierungspfad der Optionsseite selbst <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>wird durch Kombinieren von , dem Wort, ToolsOptionsPages und der Optionsseitenkategorie und dem Namen bestimmt. Wenn z. B. auf der Seite Benutzerdefinierte Optionen <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> die Kategorie "Eigene Optionsseiten" und die Seite HKEY_LOCAL_MACHINE HKEY_LOCAL_MACHINE """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

## <a name="toolsoptions-page-attributes-and-layout"></a>Werkzeuge/Optionen Seitenattribute und Layout
 Das <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut bestimmt die Gruppierung benutzerdefinierter Optionsseiten in Kategorien in der Navigationsstruktur des Dialogfelds **Optionen.** Das <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Attribut ordnet dem VSPackage, das die Schnittstelle bereitstellt, eine Optionsseite zu. Betrachten Sie das folgende Codefragment:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Dadurch wird deklariert, dass MyPackage zwei Optionsseiten bietet, OptionsPageGeneral und OptionsPageCustom. Im Dialogfeld **Optionen** werden beide Optionsseiten in der Kategorie **Eigene Optionsseiten** als **Allgemein** bzw. **Benutzerdefiniert**angezeigt.

## <a name="option-attributes-and-layout"></a>Optionsattribute und Layout
 Die benutzeroberfläche (UI), die die Seite bereitstellt, bestimmt die Darstellung von Optionen auf einer benutzerdefinierten Optionsseite. Das Layout, die Beschriftung und die Beschreibung von Optionen auf einer seite der generischen Optionen werden durch die folgenden Attribute bestimmt:

- <xref:System.ComponentModel.CategoryAttribute>bestimmt die Kategorie der Option.

- <xref:System.ComponentModel.DisplayNameAttribute>bestimmt den Anzeigenamen der Option.

- <xref:System.ComponentModel.DescriptionAttribute>bestimmt die Beschreibung der Option.

  > [!NOTE]
  > Äquivalente Attribute, SRCategory, LocDisplayName und SRDescription, verwenden Zeichenfolgenressourcen für die Lokalisierung und werden im [verwalteten Projektbeispiel](/azure/devops/integrate/index)definiert.

  Betrachten Sie das folgende Codefragment:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Die Option OptionInteger wird auf der Optionsseite als **Ganzzahloption** in der Kategorie **Eigene Optionen** angezeigt. Wenn die Option ausgewählt ist, wird die Beschreibung **"Meine Ganzzahloption "** im Beschreibungsfeld angezeigt.

## <a name="accessing-options-pages-from-another-vspackage"></a>Zugreifen auf Optionsseiten von einem anderen VSPackage aus
 Ein VSPackage, das eine Optionsseite hostet und verwaltet, kann mithilfe des Automatisierungsmodells programmgesteuert von einem anderen VSPackage aus aufgerufen werden. Im folgenden Code wird z. B. ein VSPackage als Host einer Optionsseite registriert.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Das folgende Codefragment ruft den Wert von OptionInteger von MyOptionPage ab:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Wenn <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> das Attribut eine Optionsseite registriert, wird die Seite `SupportsAutomation` unter dem AutomationProperties-Schlüssel registriert, wenn das Argument des Attributs `true`ist. Die Automatisierung untersucht diesen Registrierungseintrag, um das zugehörige VSPackage zu finden, und die Automatisierung greift dann über die Seite der gehosteten Optionen, in diesem Fall Meine Rasterseite, auf die Eigenschaft zu.

 Der Registrierungspfad der Automatisierungseigenschaft <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>wird durch Kombinieren von , dem Wort AutomationProperties und der Optionsseitenkategorie und dem Namen bestimmt. Wenn die Optionsseite z. B. die Kategorie "Meine Kategorie", den Namen "Meine Rasterseite" und die <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp enthält, verfügt die Automatisierungseigenschaft über den Registrierungsschlüssel HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp-AutomationProperties-Meine Kategorie-Meine Rasterseite.

> [!NOTE]
> Der kanonische Name" "Meine Category.My Rasterseite" ist der Wert des Unterschlüssels Name dieses Schlüssels.

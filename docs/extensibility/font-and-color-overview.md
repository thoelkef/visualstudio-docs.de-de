---
title: Schriftart und Farbe (Übersicht) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8185d5c931ccf0b3b15fba10405cf050eb7c6241
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="font-and-color-overview"></a>Schriftart und Farbe (Übersicht)
In diesem Thema wird erläutert, Schriftart und Farbe Einstellungen für Text in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Es führt auch zu die Konzepten der Kategorien und Elemente anzeigen, und es wird beschrieben, wie VSPackages und die Core-Editor Textattribute.  
  
## <a name="the-fonts-and-colors-property-page"></a>Schriftarten und Farben-Eigenschaftenseite  
 Können Sie Attribute von angezeigtem Text in verwalten die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) über die **Schriftarten und Farben** Eigenschaftenseite. Zum Suchen der **Schriftarten und Farben** Eigenschaftenseite auf die **Tools** im Menü klicken Sie auf **Optionen**. Erweitern Sie **Umgebung**, und klicken Sie dann auf **Schriftarten und Farben**.  
  
## <a name="categories-and-display-items"></a>Kategorien und Anzeigeelemente  
 Schriftarten und Farben werden in organisiert **Kategorien** und **Anzeigeelementen**.  
  
-   Ein **Kategorie** ist ein logischer oder funktionalen Container für eine Reihe von **Anzeigeelementen**.  
  
     Eine Liste der **Kategorien** befindet sich in der **Einstellungen anzeigen für** im Dropdown-Feld der **Schriftarten und Farben** Eigenschaftenseite.  
  
-   Ein **Anzeigeelements** ist eine Entität klar definierten Text z. B. einen Kommentar, eine Zeichenfolge oder eine Steuerelement-Struktur, die bei der Anzeige farbig hervorgehoben werden.  
  
 Jede **Anzeigeelements** ist eindeutig innerhalb definiert die **Kategorie** , die Sie enthält. Folglich mehr als eine **Kategorie** kann eine **Anzeigeelements** mit dem gleichen Namen.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage-Steuerelement von Schriftarten und Farben  
 Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] von VSPackages zu können:  
  
-   Definieren von Schriftart und Farbe **Kategorien**.  
  
-   Geben Sie die verwendeten Schriftarten und Farben zum Präsentieren von **Anzeigeelementen**.  
  
-   Interagieren mit der **Schriftarten und Farben** Eigenschaftenseite.  
  
-   Aggregieren mehrerer **Kategorien** gruppiert.  
  
-   Beibehalten der Änderungen in den Standardeinstellungen an.  
  
 Es gibt zwei Möglichkeiten für die Interaktion mit der Schriftart und Farbe Auswahlen in den [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Eine Möglichkeit, die Verfügbarkeitsklasse *Syntax Syntaxfarben*. Er wird von einem VSPackage, das die vorhandenen passt verwendet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Editor, um einen Sprachdienst implementieren, und erstellen eine Datenquelle mit dem Editor.  
  
     Nur ein **Kategorie** dieser Mechanismus nämlich unterstützt, wird die **Text-Editor**.  
  
-   Eine allgemeinere Alternative unterstützt alle anderen **Kategorien** und Komponenten der Benutzeroberfläche als Quellen-Editor beim Anzeigen von Text. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Core EditorText-Einstellungen  
 Schriftart und Farbe Einstellungen für den Core-Editor eines Dienstobjekts Sprache unterliegen die **Text EditorCategory** gefunden der **Einstellungen anzeigen für** im Dropdown-Feld der **Schriftarten und Farben** Eigenschaftenseite.  
  
 Bei der Arbeit mit Editoren sollten Sie verwenden spezielle Schriftart und Farbe Control-Mechanismus, der der Sprachdienst bietet, um zu steuern und Erweitern der **Texteditor** Einstellungen. Der Mechanismus wird als bezeichnet *Syntaxfarben* und bietet:  
  
-   Ein vereinfachtes Verfahren zum Verwalten von Schriftarten und Farben für Anzeigeelemente.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Eine klar definierte und optimierte farbliche Kennzeichnung-Mechanismus.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   Die Möglichkeit, beide verwenden integrierte Anzeigeelementen aus der **Text EditorCategory** und um sie zu erweitern.  
  
     Weitere Informationen finden Sie unter [wie: Verwenden integrierter Färbbare Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md) und [benutzerdefinierte Färbbare Elemente](../extensibility/internals/custom-colorable-items.md).  
  
-   Automatische Beibehaltung des aktuellen Status des sowohl integrierte und benutzerdefinierte Elemente mit Anzeigen der **Texteditor** Kategorie.  
  
 Weitere Informationen zu Syntaxfarben finden Sie unter [Syntax in ein Legacy-Sprachdienst Farbgebung](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
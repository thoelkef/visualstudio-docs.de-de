---
title: Schriftart und Farbe (Übersicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 611620b0560563cfba41b302c3e8e3611ab5a7a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888657"
---
# <a name="font-and-color-overview"></a>Schriftart und Farbe (Übersicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird erläutert, Text-Schriftart und Farbe Einstellungen in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE). Es stellt auch die Konzepte der Kategorien "und" Elemente anzeigen, und es wird beschrieben, wie VSPackages und den Haupteditor von Text-Attribute.  
  
## <a name="the-fonts-and-colors-property-page"></a>Die Schriftarten und Farben-Eigenschaftenseite  
 Sie können die Attribute des angezeigten Texts in verwalten die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) über die **Schriftarten und Farben** Eigenschaftenseite. Finden der **Schriftarten und Farben** Eigenschaftenseite auf die **Tools** Menü klicken Sie auf **Optionen**. Erweitern Sie **Umgebung**, und klicken Sie dann auf **Schriftarten und Farben**.  
  
## <a name="categories-and-display-items"></a>Kategorien und Anzeigeelemente  
 Schriftarten und Farben werden in organisiert **Kategorien** und **Anzeigeelemente**.  
  
- Ein **Kategorie** ist ein logischer oder funktionale Container für eine Reihe von **Anzeigeelemente**.  
  
   Eine Liste der **Kategorien** befindet sich in der **Einstellungen anzeigen für** Dropdown-Listenfeld, der die **Schriftarten und Farben** Eigenschaftenseite.  
  
- Ein **Anzeigeelement** ist eine klar definierte Text Entität wie z. B. einen Kommentar, eine Zeichenfolge oder eine Steuerelement-Struktur, die farbig markiert werden, wenn Sie angezeigt werden.  
  
  Jede **Anzeigeelement** ist eindeutig innerhalb definiert die **Kategorie** , die Sie enthält. Daher mehr als ein **Kategorie** kann eine **Anzeigeelement** mit dem gleichen Namen.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage-Steuerelement von Schriftarten und Farben  
 Die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSPackages zu können:  
  
- Definieren von Schriftart- und farbeinstellungen **Kategorien**.  
  
- Angeben von Schriftarten und Farben verwendet, um präsentieren **Anzeigeelemente**.  
  
- Interagieren mit der **Schriftarten und Farben** Eigenschaftenseite.  
  
- Aggregieren mehrerer **Kategorien** in Gruppen.  
  
- Beibehalten von Änderungen in den Standardeinstellungen.  
  
  Es gibt zwei Möglichkeiten für die Interaktion mit der Auswahl von Schriftart und Farbe in der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
- Eine Möglichkeit, die Verfügbarkeitsklasse *Syntax Färbung*. Hiermit wird durch ein VSPackage, das den vorhandenen passt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Editor, um eine Sprachdienst implementiert, und erstellen Sie eine Quelle-Editor.  
  
   Nur ein **Kategorie** unterstützt Sie dieser Mechanismus, d. h. die **Text-Editor**.  
  
- Eine allgemeinere Alternative unterstützt alle anderen **Kategorien** und Komponenten der Benutzeroberfläche als Quellcode-Editor beim Anzeigen von Text. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Text der Kern-Editor-Einstellungen  
 Schriftart- und farbeinstellungen Einstellungen für die Kern-Editor eines Dienstobjekts Sprache unterliegen der **Text EditorCategory** finden Sie in der **Einstellungen anzeigen für** Dropdown-Listenfeld von der **Schriftarten und Farben** Eigenschaftenseite.  
  
 Bei der Arbeit mit Editoren sollten Sie verwenden spezielle Schriftart und Farbe Mechanismus zur Zugriffskontrolle, die der Sprachdienst bereitstellt, um zu steuern und Erweitern der **Text-Editor** Einstellungen. Der Mechanismus wird als bezeichnet *Syntaxfarben* und bietet:  
  
- Ein vereinfachtes Verfahren zum Verwalten von Schriftarten und Farben von Elementen zu erstellen.  
  
   Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Ein Mechanismus, klar definierte und optimierte Farbgebung.  
  
   Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Die Möglichkeit zum Verwenden von integrierte von Anzeigeelementen aus der **Text EditorCategory** und diese zu erweitern.  
  
   Weitere Informationen finden Sie unter [Vorgehensweise: verwenden integrierten kolorierbaren Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md) und [benutzerdefinierten kolorierbaren Elemente](../extensibility/internals/custom-colorable-items.md).  
  
- Automatische Persistenz des aktuellen Zustands des sowohl integrierte und benutzerdefinierte Elemente mit angezeigt werden, die **Text-Editor** Kategorie.  
  
  Weitere Informationen zu Syntaxfarben finden Sie unter [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)


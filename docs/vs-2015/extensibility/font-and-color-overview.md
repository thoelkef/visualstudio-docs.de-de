---
title: Übersicht über Schriftart und Farbe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204350"
---
# <a name="font-and-color-overview"></a>Schriftart und Farbe – Übersicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Schriftart-und Farbeinstellungen von Text in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (IDE) erläutert. Außerdem werden die Konzepte von Kategorien und Anzeigeelementen eingeführt, und es wird beschrieben, wie VSPackages und der Core-Editor Text Attribute verwenden.  
  
## <a name="the-fonts-and-colors-property-page"></a>Die Eigenschaften Seite "Schriftarten und Farben"  
 Sie können Attribute von angezeigter Text in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) über die Eigenschaften Seite **Schriftarten und Farben** verwalten. Klicken Sie **im Menü Extras** auf **Optionen**, um die Eigenschaften Seite **Schriftarten und Farben** zu suchen. Erweitern Sie **Umgebung**, und klicken Sie dann auf **Schriftarten und Farben**.  
  
## <a name="categories-and-display-items"></a>Kategorien und Anzeigen von Elementen  
 Schriftarten und Farben sind in **Kategorien** und **Anzeigeelemente**gegliedert.  
  
- Eine **Kategorie** ist ein logischer oder funktionaler Container für eine Reihe von **Anzeigeelementen**.  
  
   Eine Liste der **Kategorien** finden Sie im Dropdown Feld **Einstellungen anzeigen für** auf der Eigenschaften Seite **Schriftarten und Farben** .  
  
- Bei einem **Anzeigeelement** handelt es sich um eine klar definierte Text Entität, z. b. einen Kommentar, eine Zeichenfolge oder eine Steuerelement Struktur, die angezeigt werden soll, wenn Sie angezeigt wird.  
  
  Jedes **Anzeigeelement** ist eindeutig in der **Kategorie** definiert, in der es enthalten ist. Folglich können mehr als eine **Kategorie** ein **Anzeigeelement** mit dem gleichen Namen aufweisen.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage-Steuerelement für Schriftarten und Farben  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Ermöglicht VSPackages Folgendes:  
  
- Definieren Sie Schriftart-und Farb **Kategorien**.  
  
- Geben Sie die Schriftarten und Farben an, mit denen **Anzeigeelemente angezeigt**werden.  
  
- Interagieren Sie mit der Eigenschaften Seite **Schriftarten und Farben** .  
  
- Aggregieren mehrerer **Kategorien** in Gruppen.  
  
- Persistente Änderungen in den Standardeinstellungen.  
  
  Es gibt zwei Möglichkeiten, mit der Schriftart-und Farbauswahl in zu interagieren [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Eine Methode wird als *Syntax Farbgebung*bezeichnet. Sie wird von einem VSPackage verwendet, das den vorhandenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor anpasst, um einen Sprachdienst zu implementieren und einen Quellen-Editor zu erstellen.  
  
   Nur eine **Kategorie** unterstützt diesen Mechanismus, nämlich den **Text-Editor**.  
  
- Eine allgemeinere Alternative unterstützt beim Anzeigen von Text alle anderen **Kategorien** und Benutzeroberflächen Komponenten, außer dem Quellen-Editor. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Text Einstellungen des Kern-Editors  
 Die Schriftart-und Farbeinstellungen für den Kern Editor eines Sprachdienst Objekts werden durch den **Text EditorCategory** gesteuert, der im Dropdown Feld **Einstellungen anzeigen für** auf der Eigenschaften Seite **Schriftarten und Farben** enthalten ist.  
  
 Beim Arbeiten mit Editoren sollten Sie den speziellen Schriftart-und Farb Steuerungsmechanismus verwenden, den der Sprachdienst zum Steuern und Erweitern der **Text-Editor** -Einstellungen bereitstellt. Der Mechanismus wird als *Syntax Farbgebung* bezeichnet und bietet Folgendes:  
  
- Ein vereinfachtes Verfahren zum Verwalten der Schriftarten und Farben von Anzeigeelementen.  
  
   Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Ein klar definierter und optimierter farbliche Mechanismus.  
  
   Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Die Möglichkeit zur Verwendung integrierter Anzeigeelemente aus der **Text-Editor Category** und deren Erweiterung.  
  
   Weitere Informationen finden Sie unter Gewusst [wie: Verwenden integrierter, colorable-Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md) und [benutzerdefinierter Elemente](../extensibility/internals/custom-colorable-items.md).  
  
- Automatische Persistenz des aktuellen Status sowohl integrierter als auch benutzerdefinierter Anzeigeelemente mit der Kategorie **Text-Editor** .  
  
  Weitere Informationen zur Syntax Färbung finden Sie [unter Syntax Farbgebung in einem Legacy Sprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Legacy Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

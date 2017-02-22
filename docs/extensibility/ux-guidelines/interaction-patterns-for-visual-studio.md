---
title: "Interaktion von Mustern f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Interaktion von Mustern f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Übersicht  
 Ein Entwurfsmuster wird in der Regel den Kern eines Entwurfs, der in bestimmten Situationen zum Lösen von Problemen mit ähnlichen Sätzen von Einschränkungen angewendet werden können. Funktion und System\-Designer verwenden diese Entwurfsmuster als Ausgangspunkt für ihre spezifische Situation angepasst werden kann.  
  
 Visual Studio verfügt über eine Bibliothek mit häufige Muster von Interaktion, die beim Erstellen von neuen Funktionen berücksichtigt werden sollten. Es gibt zwei Core Kontexten für unsere Entwurfsmuster: Visual Studio\-Client \(Devenv\) und Visual Studio Online. Für einige Probleme mit dem Entwurf ist eine weit verbreitete Muster, das in allen Situationen gut funktioniert. In vielen Fällen kann jedoch die Lösung für die Benutzeroberfläche unterscheiden, die innerhalb eines Browsers, der auf einer Client\-Anwendung gehostet wird präsentiert wird.  
  
### Visual Studio\-Client Mustertypen  
  
|Mustertyp|Beschreibung|Beispiele|  
|---------------|------------------|---------------|  
|**Muster auf Anwendungsebene**|Allgemeine Muster für die Anwendung, bestimmen oder Anwendungskontext anzeigen und zusammengesetzte und Steuerelementmuster, die darin enthaltenen enthält|-   Toolfenster<br />-   Dokumentfenster|  
|**Zusammengesetzte Muster**|Allgemeine Muster, die über Anwendungsmuster hinweg erstrecken oder einem erkannten Muster besteht aus mehreren Steuerelementen in einer unterschiedlichen Konfiguration|-   Wechseln zwischen den Ansichten<br />-   Liste\-Generatoren<br />-   Anzeigen von Daten<br />-   Benachrichtigungen<br />-   Validierung<br />-   Auswahlmodelle|  
|**Steuerelementmuster**|Einzelheiten zu wie Low\-Level\-Steuerelemente sind, verhalten sich voraussichtlich|-   Strukturansichten<br />-   In einem Datenraster\-Steuerelement bearbeiten|  
  
## Application\-Muster  
 Auf einer hohen Ebene besteht aus der Benutzeroberfläche von Visual Studio, Windows, Dialogfelder, Befehle und Symbolleisten in einer einzigen IDE. Die Visual Studio\-Hierarchie bestimmt Menüs Kontext und Laufwerke. Die wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE werden Dokumentfenster, Toolfenster, Projekte, die Befehlsstruktur, Text\-Editor, der Toolbox, das Eigenschaftenfenster und Tools \> Optionen.  
  
 Es gibt grundlegende Verwendungsmuster für jede der in der Benutzeroberfläche der IDE das wichtige Integrationspunkte:  
  
-   [Menüs und Befehlen für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Fenster Interaktionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Toolfenster](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Dokumentkonventionen-editor](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projekte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## Allgemeine Steuerelementmuster  
 Steuerelementmuster sind hauptsächlich zu Steuerelementen wie erwartet verhält. Dies ist ein Bereich, in dem Konsistenz die wichtigsten ist.  
  
 Am häufigsten verwendeten Steuerelemente in Visual Studio sollte die Windows\-Desktop\-Richtlinien befolgen. Unsere Richtlinien enthalten nur die Bereiche, in denen wir erweitern die allgemeine Konventionen mit Visual Studio\-spezifische Interaktionen oder stellen in denen wir die Richtlinien vollständig ablösen um Visual Studio entsprechend den Bedürfnissen unserer anspruchsvolle Benutzer anpassen müssen.  
  
-   [Allgemeine Steuerelementmuster für Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Allgemeine Steuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Schaltflächen und hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## Zusammengesetzte Muster  
 Es gibt eine Reihe von Möglichkeiten, die Benutzer erwarten, um Aufgaben auszuführen. Nach Möglichkeit sollten Features entworfen werden, diese Muster für die Interaktion und den visuellen Entwurf verwenden.  
  
 Es gibt viele composite\-Muster in Visual Studio einige der wichtigsten Funktionen im Hinblick auf Konsistenz sind:  
  
-   [Zusammengesetzte Muster für Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Auf Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistenz und Speichern von Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
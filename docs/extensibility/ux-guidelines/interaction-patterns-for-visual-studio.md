---
title: Interaktionsmustern für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="interaction-patterns-for-visual-studio"></a>Interaktionsmustern für Visual Studio
## <a name="overview"></a>Übersicht  
 Ein Entwurfsmuster ist im Allgemeinen das Kernstück des ein Entwurf, der in bestimmten Situationen auf, die Behebung von Problemen mit ähnlichen Sätzen von Einschränkungen angewendet werden kann. Funktion und System-Designer verwenden Sie diese Entwurfsmuster als Ausgangspunkt für ihre spezifische Situation angepasst werden kann.  
  
 Visual Studio verfügt über eine Bibliothek mit allgemeinen interaktionsmustern, die beim Erstellen der neuer Funktionen berücksichtigt werden sollten. Es gibt zwei Core Kontexten für unsere Entwurfsmuster: Visual Studio-Clients (Devenv) und Visual Studio Online. Für einige Probleme mit dem Entwurf ist eine weit verbreitete Muster, das in allen Situationen optimal funktioniert. In vielen Fällen kann jedoch die Lösung für UI abweichen, der präsentiert wird in einem Browser und, der auf eine Clientanwendung gehostet wird.  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio-Client-Mustertypen  
  
|Mustertyp|Beschreibung|Beispiele|  
|------------------|-----------------|--------------|  
|**Muster auf Anwendungsebene**|Allgemeine Muster für die Anwendung, bestimmen oder Anwendungskontext anzeigen und zusammengesetzte und Steuerelementmuster, die darin enthaltenen enthält allgemeine|-Windows tool<br />-Windows Dokument|  
|**Zusammengesetzte Muster**|Allgemeine Muster, die über Anwendungsmuster hinweg erstrecken oder einem erkannten Muster setzt sich aus mehrere Steuerelemente in einer Konfiguration mit distinct|-Wechseln zwischen den Ansichten<br />-List-Generatoren<br />– Anzeigen von Daten<br />-Benachrichtigungen<br />-Überprüfung<br />-Auswahl Modelle|  
|**Steuerelementmuster**|Einzelheiten zu wie auf niedriger Ebene Steuerelemente werden erwartet, dass das Verhalten|-Struktur-Ansichten<br />-Bearbeitung in einem Datenraster-Steuerelement|  
  
## <a name="application-patterns"></a>Anwendungsmuster  
 Auf hoher Ebene besteht aus Visual Studio-Benutzeroberfläche, Windows, Dialogfelder, Befehle und Symbolleisten in einer einzigen IDE. Die Visual Studio-Hierarchie bestimmt Kontext und Laufwerke Menüs. Die wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE werden Dokumentfenster, Toolfenster, Projekte, die Befehlsstruktur, Text-Editor, der Toolbox, das Fenster "Eigenschaften" und Tools > Optionen.  
  
 Es gibt für jede der in der Benutzeroberfläche der IDE die wichtigsten Integrationspunkte grundlegende Verwendungsmuster:  
  
-   [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Fenster Interaktionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Toolfenster](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Dokument-Editor-Konventionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projekte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Allgemeine Steuerelementmustern  
 Steuerelementmuster werden hauptsächlich zur Nutzung einzelner Steuerelemente Verhalten erwartet werden. Dies ist ein Bereich in der Konsistenz besonders wichtig ist.  
  
 Am häufigsten verwendeten Steuerelemente in Visual Studio sollte die Windows-Desktop-Richtlinien beachtet werden. Unsere Richtlinien enthalten nur Bereiche, in denen wir erweitern, allgemeine Konventionen mit Visual Studio-spezifische Aktivitäten oder Orte, die in denen wir die Richtlinien vollständig ablösen um Visual Studio entsprechend den Bedürfnissen unserer anspruchsvolle Benutzer anpassen müssen.  
  
-   [Allgemeine Steuerelementmuster für Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Allgemeine Steuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Schaltflächen und Links](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Zusammengesetzte Muster  
 Es gibt zahlreiche Möglichkeiten, die Benutzer erwarten, um Aufgaben auszuführen. Nach Möglichkeit sollten Funktionen so entworfen werden, diese Muster sowohl für die Interaktion und den visuellen Entwurf verwendet.  
  
 Dafür gibt es viele zusammengesetzte Muster in Visual Studio zu den wichtigsten Feldern im Hinblick auf die Konsistenz sind:  
  
-   [Zusammengesetzte Muster für Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Auf Objekt Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistenz und Speichern der Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
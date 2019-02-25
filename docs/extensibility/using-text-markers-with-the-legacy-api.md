---
title: Verwenden von Textmarkierungen mit der Legacy-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6a3807dc91b129ba4b337f57e3f857e4f379581
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696688"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Verwenden von Textmarkierungen mit der Legacy-API
Eine textmarkierung ist einen unverankerten Textbereich in einem Puffer, der die Anzeige beeinträchtigen können und das Verhalten eines Bereichs des Texts. Marker sind Haltepunkte, Lesezeichen, wellenförmige unterstreichungen und schreibgeschützter Bereiche. Textmarkierungen unterscheiden sich grundsätzlich von Syntaxfarben. Farben für Syntax ist eine schnelle Möglichkeit, um die Sprachsyntax zu kommunizieren, die dem Textbereich zugeordnet ist. Farben für Syntax wird in der Regel angefordert, wenn Windows den Bildschirm zeichnet neu, wenn Geschwindigkeit von Bedeutung ist. Farben für Syntax ändert nur die Farbe des Texts. Textmarkierungen können viele andere Eigenschaften des Texts ändern. Textmarkierungen "float" und besonderes Verhalten angewendet werden können und färben.

 Erstellen Sie aufgrund des Leistungsoverheads Textmarkierungen zugeordnet wird nicht viele Marker für Ihre Textpuffer. Marker wird aktualisiert, wenn ein Benutzer den Inhalt des Puffers bearbeitet.

> [!NOTE]
>  Benutzer können die Farbe des einen sichtbaren Markertyp, aber nicht die Form und Stil ändern. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialogfeld Optionen](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

## <a name="related-topics"></a>Verwandte Themen

| Titel | Beschreibung |
| - | - |
| [Vorgehensweise: Standard-Text-Marker hinzufügen](../extensibility/how-to-add-standard-text-markers.md) | Beschreibt das Hinzufügen von bereitgestellten Typ des Markers eine standard-Text der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf eine Textansicht-Kern-Editor. |
| [Vorgehensweise: Implementieren von Fehlermarker](../extensibility/how-to-implement-error-markers.md) | Beschreibt, wie Sie eine Instanz der Implementierung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Marker, der verwendet wird, um Fehler anzugeben, mit einer roten Wellenlinie unterstrichen. |
| [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md) | Beschreibt das Erstellen und eine Textansicht ein Markertyps benutzerdefinierten Text hinzuzufügen. |
| [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md) | Erläutert das Hinzufügen von Textmarkierungen. |
| [Im Core-Editor](../extensibility/inside-the-core-editor.md) | Beschreibt die Funktionen von der Kern-Editor, und enthält ausführliche Informationen zum Anpassen der Kern-Editor. |
| [Editor-Funktionen](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198) | Beschreibt die Funktionen zur Verfügung, in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor. |

## <a name="reference"></a>Referenz
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> Bietet einen einheitlichen Mechanismus zum Abrufen von Informationen über einen bestimmten textmarkertyp, ob vom Editor vordefiniert oder durch ein VSPackage registriert.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker> Bietet Zugriff auf und passt die Position eines textmarkers in einem Textpuffer mithilfe der zweidimensionale Koordinaten.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Stellt Methoden zum Verwalten von textmarkern bereit.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Stellt Rückrufe an die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE und andere Prozesse, die verwendet werden, um eine textmarkierung anzupassen.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> Erweitert die Funktionalität, die über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> -Schnittstelle durch Bereitstellen zusätzlicher Rückrufe.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> Erweitert die Funktionalität, die über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> -Schnittstelle durch Bereitstellen zusätzlicher Rückrufe.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet> Können einen Markertyp aus, um festzustellen, ob andere Markertypen den gleichen Satz von Farben verwenden.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Stellt den Kontext für Textmarker im kerneditor bereit. Für jede textmarkertyp, die in der Kern-Editor ist, erstellt die IDE eine Separate <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Objekt.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler> Ein Handler, der für Marker angegeben ist, dessen Symbole Drag & Drop-Bearbeitung unterstützt. Ein Symbol ist ein Symbol, das die Position eines Markers angibt.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> Gibt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> -Schnittstelle aus einem Dienst, der einen Text Marker aus, die anderen VSPackages bereitstellt.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker> Bietet Zugriff auf und passt die Position eines textmarkers in einem Textpuffer mithilfe der eindimensionale Koordinaten. Wenn es möglich ist, verwenden Sie diese Schnittstelle nicht.
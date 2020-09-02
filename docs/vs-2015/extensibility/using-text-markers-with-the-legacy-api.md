---
title: Verwenden von Text Markern mit der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695479"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Verwenden von Textmarkern mit der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Textmarker ist ein unverankerter Textbereich in einem Puffer, der die Anzeige und das Verhalten eines Text Bereichs beeinflussen kann. Marker schließen Haltepunkte, Lesezeichen, wellenförmige Unterstreichungen und schreibgeschützte Bereiche ein. Text Marker unterscheiden sich im Grunde von der Syntax Farbgebung. Die Syntax Farbgebung ist eine schnelle Möglichkeit, um die Sprachsyntax zu kommunizieren, die einem Textbereich zugeordnet ist. Die Syntax Farbgebung wird in der Regel angefordert, wenn Windows den Bildschirm zeichnet, wenn die Geschwindigkeit wichtig ist. Syntax Färbung ändert nur die Textfarbe. Textmarker können viele andere Texteigenschaften ändern. Text Marker können "float" sein und spezielles Verhalten und Farbgebung anwenden.  
  
 Erstellen Sie aufgrund des Leistungs Aufwands, der Text Markern zugeordnet ist, nicht viele Marker für die Text Puffer. Jeder Marker wird jedes Mal aktualisiert, wenn ein Benutzer den Pufferinhalt bearbeitet.  
  
> [!NOTE]
> Benutzer können die Farbe eines sichtbaren Markertyps ändern, jedoch nicht seine Form und ihren Stil. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialog Feld "Optionen](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)".  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|BESCHREIBUNG|  
|-----------|-----------------|  
|[Vorgehensweise: Hinzufügen von Standardtextmarkierungen](../extensibility/how-to-add-standard-text-markers.md)|Beschreibt, wie einer Textansicht ein Standardtext Markertyp hinzugefügt wird, der vom Core-Editor bereitgestellt wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[Vorgehensweise: Implementieren von Fehlermarkierungen](../extensibility/how-to-implement-error-markers.md)|Beschreibt, wie eine Instanz des Markers implementiert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird, die verwendet wird, um Fehler mithilfe von roten Wellen Strichen anzugeben.|  
|[Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen](../extensibility/how-to-create-custom-text-markers.md)|Beschreibt, wie ein benutzerdefinierter Text Markertyp zu einer Textansicht erstellt und hinzugefügt wird.|  
|[Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)|Erläutert das Hinzufügen von Text Markern.|  
|[Im Core-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die Funktionen des Kern-Editors und bietet ausführliche Informationen zum Anpassen des Kern-Editors.|  
|[Editor-Funktionen](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Beschreibt die Funktionen, die im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kern-Editor verfügbar sind.|  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Bietet einen einheitlichen Mechanismus zum Abrufen von Informationen über einen bestimmten Text Markertyp, unabhängig davon, ob dies vom Editor vordefiniert oder durch ein VSPackage registriert wird.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Bietet den Zugriff auf und passt die Position eines Text Markers in einem Text Puffer an, indem zweidimensionale Koordinaten verwendet werden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Stellt Methoden zum Verwalten von Textmarkern bereit.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Stellt Rückrufe für die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE und andere Prozesse zur Verfügung, die zum Anpassen eines Text Markers verwendet werden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Erweitert die Funktionalität, die über die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle verfügbar ist, indem zusätzliche Rückrufe bereitgestellt werden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Erweitert die Funktionalität, die über die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle verfügbar ist, indem zusätzliche Rückrufe bereitgestellt werden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Aktiviert einen Markertyp, um zu bestimmen, ob andere Markertypen denselben Satz von Farben gemeinsam verwenden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Stellt Kontext für Textmarker im Kern-Editor bereit. Für jeden Text Markertyp, der sich im Kern-Editor befindet, erstellt die IDE ein separates- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Objekt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Ein Handler, der für Marker bereitgestellt wird, deren Glyphen Drag & Drop-Bearbeitung unterstützen. Ein Symbol ist ein Symbol, das die Position eines Markers angibt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Gibt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> Schnittstelle von einem Dienst zurück, der einem anderen VSPackages Textmarker bereitstellt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Bietet Zugriff auf und passt die Position eines Text Markers in einem Text Puffer mithilfe eindimensionaler Koordinaten an. Verwenden Sie diese Schnittstelle nicht, wenn dies möglich ist.

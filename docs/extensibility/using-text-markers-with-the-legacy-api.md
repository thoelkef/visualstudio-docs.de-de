---
title: Die Legacy-API Text Marker mit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98c889bc1bc128a941f726348781a633799475de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>Verwenden von Text Marker mit der Legacy-API
Ein Marker Text ist, einen unverankerten Textbereich in einem Puffer, der die Anzeige beeinträchtigen können und das Verhalten eines Bereichs des Texts. Marker sind Haltepunkte, Lesezeichen, wellenförmige Unterstreichung und nur-Lese Regionen. Text-Marker sind im Grunde Syntaxfarben unterscheiden. Syntaxfarben ist eine schnelle Möglichkeit, die Sprachsyntax kommunizieren, die dem Textbereich zugeordnet ist. Syntaxfarben wird in der Regel angefordert, wenn Windows den Bildschirm aktualisiert, wenn die Geschwindigkeit wichtig ist. Syntaxfarben ändert nur die Farbe des Texts. Text-Marker können viele andere Texteigenschaften ändern. Text-Marker "float" und besonderes Verhalten angewendet werden können und Farbgebung.  
  
 Erstellen Sie aufgrund der zusätzlichen Verwaltungsaufwand ist mit Text Marker nicht viele Marker für Ihre Textpuffer. Marker wird jedes Mal aktualisiert, dass ein Benutzer den Inhalt des Puffers bearbeitet.  
  
> [!NOTE]
>  Benutzer können die Farbe einen Markertyp sichtbar, aber nicht seine Form und des Stils ändern. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Optionen (Dialogfeld)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Hinzufügen von Standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)|Beschreibt, wie Sie einen standard-Text-Markertyp gebotenen Hinzufügen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor eine anzuzeigende Text.|  
|[Vorgehensweise: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)|Beschreibt, wie eine Instanz der Implementierung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Marker, der verwendet wird, um Fehler weisen darauf hin, mit roten Wellenlinien unterstrichen.|  
|[Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker](../extensibility/how-to-create-custom-text-markers.md)|Beschreibt das Erstellen und eine Textansicht einen Markertyp benutzerdefinierten Text hinzuzufügen.|  
|[Vorgehensweise: Verwenden von Text-Marker](../extensibility/how-to-use-text-markers.md)|Erläutert, wie Text Marker hinzufügen.|  
|[In der Core-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die Funktionen des Editors Core und bietet ausführliche Informationen zum Anpassen des Core-Editors.|  
|[Editor-Funktionen](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Beschreibt die Funktionen, die verfügbar sind, in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor.|  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Bietet einen einheitlichen Mechanismus zum Abrufen von Informationen über einen Markertyp bestimmtem Text, ob vom Editor vordefiniert oder durch ein VSPackage registriert.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Bietet Zugriff auf und passt die Position des ein Marker Text in einem Textpuffer mithilfe von zweidimensionalen Koordinaten an.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Stellt Methoden zum Verwalten von Text-Marker.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Rückrufe bietet die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE und anderen Prozessen, die verwendet werden, um einen Marker Text anzupassen.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Erweitert die Funktionalität, die über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle durch zusätzliche Rückrufe bereitstellen.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Erweitert die Funktionalität, die über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle durch zusätzliche Rückrufe bereitstellen.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Können einen Markertyp aus, um festzustellen, ob andere Markertypen den gleichen Satz von Farben verwenden.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Stellt den Kontext für Text Marker in der Core-Editor bereit. Für jeden Text Marker, die in der Core-Editor ist, erstellt die IDE eine Separate <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Objekt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Ein Handler, der Marker aus Gründen, dessen Symbole Drag & Drop-Bearbeitung unterstützen. Ein Symbol ist ein Symbol, das die Position des ein Marker angibt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Gibt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> Schnittstelle von einem Dienst, der einen Text Marker aus, die anderen VSPackages bereitstellt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Bietet Zugriff auf und passt die Position des ein Marker Text in einem Textpuffer mithilfe von eindimensionalen Koordinaten an. Wenn es möglich ist, verwenden Sie diese Schnittstelle nicht.
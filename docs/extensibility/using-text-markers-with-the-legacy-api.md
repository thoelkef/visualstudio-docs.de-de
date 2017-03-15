---
title: "Verwenden von Text Marker mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Text-Marker"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Verwenden von Text Marker mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Textmarkierung ist ein unverankerter Textbereich in einem Puffer, der die Darstellung und das Verhalten eines Textbereichs auswirken kann.  Marker sind Haltepunkte, Lesezeichen, wellenförmige Unterstreichung und schreibgeschützte Bereiche.  Textmarkierungen Syntaxfarbe werden im Allgemeinen unterscheidet.  Syntaxfarbe ist eine schnelle Möglichkeit, die Sprachsyntax mitzuteilen, die mit einem Textbereich zugeordnet ist.  Syntaxfarbe wird im Allgemeinen angefordert, wenn Fenster auf dem Bildschirm neu streicht, wenn die Geschwindigkeit wichtig ist.  Syntaxfarbe ändert nur die Farbe des Texts.  Textmarkierungen können viele andere Texteigenschaften ändern.  Textmarkierungen ausführen „float“ ein, und übernehmen spezielles Verhalten und Farbton.  
  
 Aufgrund des Leistungsaufwand, der mit Textmarkierungen zugeordnet ist, stellen Sie nur wenige Marker für die Textpuffer.  Jeder Marker wird jedes Mal aktualisiert, dem ein Benutzer den Inhalt des Puffers behandelt.  
  
> [!NOTE]
>  Benutzer können die Farbe eines sichtbaren Typs Marker Form und seine jedoch nicht ändern.  Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md)|Beschreibt, wie ein Standardwert textmarkierungs " hinzugefügt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors aus einer Textansicht.|  
|[Gewusst wie: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)|Beschreibt, wie eine Instanz des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Markers implementiert, der verwendet wird, um den Fehler anzugeben, indem rote wellenförmige Unterstreichung verwendet.|  
|[Gewusst wie: Erstellen von benutzerdefinierten Text Marken](../extensibility/how-to-create-custom-text-markers.md)|Beschreibt, wie ein benutzerdefinierter Typ Textmarkierungs einer Textansicht erstellt und hinzugefügt wird.|  
|[Gewusst wie: Verwenden von Text\-Marker](../extensibility/how-to-use-text-markers.md)|Erläutert die Verwendung von Textmarkierungen hinzugefügt wird.|  
|[In der Core\-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die Funktionen des zentralen editors und stellt Informationen darüber bereit, wie der Kern des Editors anzupassen.|  
|[Editor Features](http://msdn.microsoft.com/de-de/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Beschreibt die Funktionen, die im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors verfügbar sind.|  
  
## Verweis  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Stellt einen einheitlichen Mechanismus zum Abrufen von Informationen über einen bestimmten Typ bereit Textmarkierungs vordefiniert, ob vom Editor oder einem VSPackage registriert.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Bietet Zugriff auf und passt die Position einer Textmarkierung in einem Textpuffer mit einem zweidimensionalen Koordinaten.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Stellt Methoden zum Verwalten von Textmarkierungen bereit.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Stellt Rückrufe zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE und anderen Prozessen bereit, die verwendet werden, um eine Textmarkierung anzupassen.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Erweitert die Funktionen, die von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle verfügbar ist, indem er weitere Rückrufe bereitstellt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Erweitert die Funktionen, die von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle verfügbar ist, indem er weitere Rückrufe bereitstellt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Aktiviert einen Marker, um zu bestimmen, ob weitere Typen von Markern den gleichen Satz von Farben freigeben.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Stellt Kontext für Textmarkierungen im Kern des Editors bereit.  Für jeden Typ Textmarkierungs im Kern des Editors ist, erstellt die IDE ein separates <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>\-Objekt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Ein Handler für Marker bereitgestellt wird, deren Symbole der Drag & Drop\-Bearbeiten unterstützen.  Ein Symbol ist ein Symbol, das die Position einer Markierung angibt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Gibt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>\-Schnittstelle von einem Dienst zurück zu anderen Textmarkierungen VSPackages bereitstellt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Bietet Zugriff auf und passt die Position einer Textmarkierung in einem Textpuffer mithilfe von eindimensionalen Koordinaten.  Wenn es möglich ist, verwenden Sie diese Schnittstelle nicht.
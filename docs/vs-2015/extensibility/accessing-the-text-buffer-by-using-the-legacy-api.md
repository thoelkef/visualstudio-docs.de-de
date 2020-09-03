---
title: Zugreifen auf den Text Puffer mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185007"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Zugreifen auf den Textpuffer mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Text ist für die Verwaltung von Textstreams und Datei Persistenz verantwortlich. Obwohl der Puffer andere Formate lesen oder schreiben kann, erfolgt die gesamte normale Kommunikation mit dem Puffer mithilfe von Unicode. In den Legacy-APIs kann der Text Puffer entweder ein ein-oder ein zweidimensionales Koordinatensystem verwenden, um Zeichen Positionen im Puffer zu identifizieren.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Koordinatensysteme mit einer und zwei Dimensionen  
 Eine eindimensionale Koordinaten Position basiert auf der Position eines Zeichens vom ersten Zeichen im Puffer, z. b. 147. Sie verwenden die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstelle, um auf eine eindimensionale Position im Puffer zuzugreifen. Ein zweidimensionales Koordinatensystem basiert auf Zeilen-und Index Paaren. Beispielsweise würde ein Zeichen im Puffer um 43, 5 in Zeile 43, fünf Zeichen rechts vom ersten Zeichen in dieser Zeile. Sie greifen mithilfe der-Schnittstelle auf einen zweidimensionalen Speicherort im Puffer zu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Sowohl die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> -Schnittstelle als auch die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstelle werden durch das Text Puffer Objekt () implementiert, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> und auf Sie kann über zugegriffen werden `QueryInterface` . Das folgende Diagramm zeigt diese und andere Schlüssel Schnittstellen in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![TextBuffer-Objekt](../extensibility/media/vstextbuffer.gif "vstextbuffer beteiligt ist")  
Text Puffer Objekt  
  
 Obwohl beide Koordinatensysteme im Text Puffer funktionieren, sind Sie für die Verwendung zweidimensionaler Koordinaten optimiert. Ein eindimensionales Koordinatensystem kann einen Leistungs Aufwand verursachen. Verwenden Sie daher nach Möglichkeit das zweidimensionale Koordinatensystem.  
  
 Die zweite Aufgabe des Text Puffers ist die Datei Persistenz. Hierzu implementiert das Text Puffer Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und fungiert als Dokument Datenobjekt-Komponente für Projekt Elemente und andere Umgebungs Komponenten, die an der Persistenz beteiligt sind. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projekt Elementen](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ändern der Ansichtseinstellungen mit der Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Erläutert, wie Sie Ansichts Einstellungen mithilfe der Legacy-API ändern.  
  
 [Überwachen der globalen Einstellungen mit dem Text-Manager](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der Text-Manager zum Überwachen von globalen Einstellungen verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Im Core-Editor](../extensibility/inside-the-core-editor.md)

---
title: Zugreifen auf den Textpuffer mithilfe der Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84bf79ea19fc0867643ce3e8ee6db0a645d9a0dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099472"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Zugreifen auf den Textpuffer mithilfe der Legacy-API
Der Text ist zuständig für das Verwalten von Textstreams und Datei-Dauerhaftigkeit. Obwohl der Puffer Lese- oder Schreibzugriff anderen Formaten alle normalen Kommunikation mit dem Puffer mithilfe von Unicode ausgeführt wird. In die legacy-APIs können die den Textpuffer ein- oder in einem zweidimensionalen Koordinatensystem um Zeichenpositionen im Puffer zu identifizieren.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimension ein und zwei Koordinatensysteme  
 Eine eindimensionale Koordinatenposition basiert auf ein Zeichen Position vom ersten Zeichen im Puffer, z. B. 147. Sie verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstelle, um den Zugriff auf eine eindimensionale Speicherort im Puffer. Ein zweidimensionales Koordinatensystem basiert auf Linien- und Index-Paaren. Beispielsweise wäre ein Zeichen im Puffer, ab der 43, 5 in Zeile 43, fünf Zeichen rechts von das erste Zeichen in dieser Zeile. Sie Zugriff auf eine zweidimensionale Ort in den Puffer mit den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle. Sowohl die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstellen werden von der TextBuffer-Objekt implementiert (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) und kann voneinander zugegriffen werden, indem `QueryInterface`. Das folgende Diagramm zeigt diese und andere wichtigsten Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![TextBuffer-Objekt](../extensibility/media/vstextbuffer.gif "VsTextBuffer")  
TextBuffer-Objekt  
  
 Obwohl entweder Koordinatensystem in den Textpuffer funktioniert, ist es optimiert, um zweidimensionalen Koordinaten zu verwenden. Ein eindimensionales Koordinatensystem können Verwaltungsaufwand erstellen. Verwenden Sie daher die zweidimensionale Koordinatensystem wann immer möglich.  
  
 Der Text des Puffers zweite Verantwortung ist die Datei Persistenz. Zu diesem Zweck die TextBuffer-Objekt implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und fungiert als die Daten Objektkomponente für Projektelemente angezeigt und andere Persistenz beteiligten Komponenten. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ändern Einstellungen anzeigen, über die Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Erläutert das Anzeigen von Einstellungen mithilfe der legacy-API zu ändern.  
  
 [Verwenden die Text-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erklärt, wie der Text-Manager zum Überwachen von globaler Einstellungen...  
  
## <a name="see-also"></a>Siehe auch  
 [In der Core-Editor](../extensibility/inside-the-core-editor.md)
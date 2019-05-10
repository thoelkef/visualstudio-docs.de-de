---
title: Zugreifen auf den Textpuffer mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dc331e06d1e82928f5c608d5b009258beb48dcc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844017"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Zugriff auf den Textpuffer mithilfe der legacy-API
Der Text ist für die Verwaltung von Text-Streams und dateipersistenz zuständig. Auch wenn der Puffer Lese- oder Schreibzugriff auf andere Formate, erfolgt die gesamte normale Kommunikation mit dem Puffer mithilfe von Unicode. In die legacy-APIs können das den Textpuffer entweder ein- oder einem zweidimensionalen Koordinatensystem um Zeichen im Puffer zu identifizieren.

## <a name="one--and-two-dimension-coordinate-systems"></a>1 und 2-Dimension Koordinatensysteme
 Eine eindimensionale Koordinatenposition basiert auf ein Zeichen, die Position vom ersten Zeichen im Puffer, z. B. 147. Sie verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstelle, um einen eindimensionalen Position im Puffer zuzugreifen. Ein zweidimensionales Koordinatensystem basiert auf Zeilen- und Index-Paaren. Beispielsweise wäre ein Zeichen im Puffer, an die 43, 5 in Zeile 43 fünf Zeichen rechts des ersten Zeichens in dieser Zeile. Sie Zugriff auf die eine zweidimensionale Position im Puffer mithilfe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle. Sowohl die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstellen werden implementiert, indem Sie das Textpufferobjekt (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) und voneinander zugegriffen werden kann, um mithilfe von `QueryInterface`. Das folgende Diagramm zeigt diese und andere wichtigsten Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![TextBuffer-Objekt](../extensibility/media/vstextbuffer.gif "VsTextBuffer") TextBuffer-Objekt

 Obwohl entweder Koordinatensystem im Textpuffer funktioniert, ist es optimiert um zweidimensionale Koordinaten zu verwenden. Ein eindimensionales Koordinatensystem können Mehraufwand an Leistung erstellen. Verwenden Sie daher die zweidimensionale Koordinatensystem, wann immer möglich.

 Der Text des Puffers zweite Aufgabe ist die dateipersistenz. Zu diesem Zweck das Textpufferobjekt implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und fungiert als die Dokument-Objekt-Komponente für Projektelemente und anderen Komponenten für Persistenz beteiligt. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>In diesem Abschnitt
- [Ändern Sie Anzeigeeinstellungen, indem Sie mithilfe der legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md) wird erläutert, wie Anzeigeeinstellungen, die mit der legacy-API ändern.

- [Verwenden Sie den TextManager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md) wird erläutert, wie der Text-Manager verwenden, um globale Einstellungen zu überwachen.

## <a name="see-also"></a>Siehe auch
- [In der Kern-editor](../extensibility/inside-the-core-editor.md)
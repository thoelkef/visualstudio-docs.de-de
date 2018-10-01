---
title: Zugreifen auf den Textpuffer mithilfe der Legacy-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e89b91dbacf60df034ac7ce3653c25c2cae7ab3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520809"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Zugreifen auf den Textpuffer mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [den Zugriff auf den Textpuffer mithilfe der Legacy-API](https://docs.microsoft.com/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api).  
  
Der Text ist für die Verwaltung von Text-Streams und dateipersistenz zuständig. Auch wenn der Puffer Lese- oder Schreibzugriff auf andere Formate, erfolgt die gesamte normale Kommunikation mit dem Puffer mithilfe von Unicode. In die legacy-APIs können das den Textpuffer entweder ein- oder einem zweidimensionalen Koordinatensystem um Zeichen im Puffer zu identifizieren.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>1 und 2-Dimension Koordinatensysteme  
 Eine eindimensionale Koordinatenposition basiert auf ein Zeichen, die Position vom ersten Zeichen im Puffer, z. B. 147. Sie verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstelle, um einen eindimensionalen Position im Puffer zuzugreifen. Ein zweidimensionales Koordinatensystem basiert auf Zeilen- und Index-Paaren. Beispielsweise wäre ein Zeichen im Puffer, an die 43, 5 in Zeile 43 fünf Zeichen rechts des ersten Zeichens in dieser Zeile. Sie Zugriff auf die eine zweidimensionale Position im Puffer mithilfe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle. Sowohl die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Schnittstellen werden implementiert, indem Sie das Textpufferobjekt (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) und voneinander zugegriffen werden kann, um mithilfe von `QueryInterface`. Das folgende Diagramm zeigt diese und andere wichtigsten Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![TextBuffer-Objekt](../extensibility/media/vstextbuffer.gif "VsTextBuffer")  
TextBuffer-Objekt  
  
 Obwohl entweder Koordinatensystem im Textpuffer funktioniert, ist es optimiert um zweidimensionale Koordinaten zu verwenden. Ein eindimensionales Koordinatensystem können Mehraufwand an Leistung erstellen. Verwenden Sie daher die zweidimensionale Koordinatensystem, wann immer möglich.  
  
 Der Text des Puffers zweite Aufgabe ist die dateipersistenz. Zu diesem Zweck das Textpufferobjekt implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und fungiert als die Dokument-Objekt-Komponente für Projektelemente und anderen Komponenten für Persistenz beteiligt. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ändern der Ansichtseinstellungen mit der Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Erläutert das Ändern der Anzeigeeinstellungen, die mit der legacy-API.  
  
 [Überwachen der globalen Einstellungen mit dem Text-Manager](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der Text-Manager zum Überwachen von globaler Einstellungen...  
  
## <a name="see-also"></a>Siehe auch  
 [Im Core-Editor](../extensibility/inside-the-core-editor.md)


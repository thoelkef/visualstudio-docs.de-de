---
title: "Zugriff auf den Textpuffer mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Textpuffer"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Zugriff auf den Textpuffer mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Text wird zur Verwaltung von Textstreams Aus Datei und Dauerhaftigkeit verantwortlich.  Obwohl der Puffer andere Formate lesen oder schreiben kann, wird die normale Kommunikation mit dem Puffer ausgeführt, indem Unicode verwendet.  Im Legacy API, kann der Textpuffer oder ein zweidimensionales Koordinatensystem verwenden, um Speicherorte Zeichen im Puffer zu identifizieren.  
  
## Ein Zwei\-Dimension und Koordinatensysteme  
 Eine eindimensionale Koordinatenposition basiert auf einer Zeichenstelle vom ersten Zeichen im Puffer, z. B. 147.  Mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>\-Schnittstelle, um einen eindimensionalen Position im Puffer zuzugreifen.  Ein zweidimensionales Koordinatensystem basiert auf Zeilen\- und Index.  Beispielsweise würde ein Zeichen im Puffer für Zeile bei 43, 5, 43 fünf Zeichen rechts vom ersten Zeichens in der Zeile sein.  Sie greifen auf einem zweidimensionalen Position im Puffer mithilfe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>\-Schnittstelle.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> werden und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>\-Schnittstellen im Textpuffer Objekt \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) implementiert und können voneinander zugegriffen werden, indem `QueryInterface`verwendet.  Das folgende Diagramm zeigt diese und andere Tasten auf Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>an.  
  
 ![TextBuffer&#45;Objekt](~/docs/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Textpuffer Objekt  
  
 Obwohl ein Koordinatensystem im Textpuffer arbeitet, wird sie optimiert, um zweidimensionale Koordinaten zu verwenden.  Ein eindimensionales Koordinatensystem kann Leistungsaufwand erstellen.  Verwenden Sie daher das Koordinatensystem zweidimensionale, wann immer dies möglich ist.  
  
 Die Verantwortung des Textpuffers Dauerhaftigkeit Datei zweiten ist.  Dazu implementiert das Textpuffer Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und fungiert als Dokumenten das angegebene Channeldatenobjekt Komponente für die Projektelemente Umgebung und andere Komponenten auf, die in der Beibehaltung beteiligt sind.  Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md).  
  
## In diesem Abschnitt  
 [Ändern die Ansicht mit der Legacy\-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Erklärt, wie mithilfe des Einstellungen anzeigen Legacy API geändert wird.  
  
 [Verwenden die Text\-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der Text Manager verwendet, um globale Einstellungen zu überwachen.  
  
## Siehe auch  
 [In der Core\-Editor](../extensibility/inside-the-core-editor.md)
---
title: "Modell f&#252;r Source Control-Pakete | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellensteuerelement-Modell [Visual Studio SDK]"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Modell f&#252;r Source Control-Pakete
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im folgenden Modell stellt ein Beispiel für eine Implementierung der Quellcodeverwaltung dar.  Im Modell finden Sie unter Schnittstellen, die Sie implementieren müssen, und die Umgebung Dienste, die Sie aufrufen müssen.  Wie alle Dienste rufen Sie die Methoden eine bestimmte Schnittstelle an, dass Sie über den Dienst abgerufen.  Die Namen von Klassen gekennzeichnet werden, um sie leichter, festzustellen, wie die Quellcodeverwaltung ausgeführt wird.  
  
 ![SCC&#95;TUP&#45;Beispiele](~/docs/extensibility/internals/media/scc_tup.gif "SCC\_TUP")  
Beispiels\-Quellcodeverwaltungs\-Projekt  
  
## Schnittstellen  
 Sie können die Quellcodeverwaltung für die neuen Projekttypen in Visual Studio mit der Liste der Schnittstellen implementieren, die in der folgenden Tabelle aufgeführt sind.  
  
|Schnittstelle|Verwendung|  
|-------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wird von Projekten und Editoren, bevor eine modifizierte \(\) \- Dateien speichern oder ändern.  Diese Schnittstelle wird mithilfe des <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst zugegriffen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wird von Projekten Berechtigung anfordert, Hinzufügen, Entfernen oder Umbenennen einer Datei oder ein Verzeichnis.  Diese Schnittstelle wird auch von Projekten, die Umgebung zu informieren aufgerufen, wenn ein erkanntes hinzufügen, entfernen oder umbenennen Aktion abgeschlossen ist.  Es wird mithilfe des <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> Dienst zugegriffen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementiert durch jede Entität, die registriert benachrichtigt werden, wenn Projekte hinzufügen, Umbenennen oder Entfernen einer Datei oder ein Verzeichnis.  Um für die Ereignisbenachrichtigung <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>Aufrufs registrieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wird von Projekten mit dem Paket die Quellcodeverwaltung zu registrieren und Informationen über den Status der Quellcodeverwaltung abrufen.  Diese Schnittstelle wird mithilfe des <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst zugegriffen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Wird vom Projekt auf Quellcodeverwaltung informationsanforderungen zu Dateien reagiert und Abrufen der Einstellungen der Quellcodeverwaltung für die Projektdatei erforderlich.|  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Unterstützung von Datenquellen\-Steuerelement](../../extensibility/internals/supporting-source-control.md)
---
title: "Modell für Steuerelement Quellpakete | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8dacc0a3dfc230085c7575960238711d16d1ef8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="model-for-source-control-packages"></a>Modell für die Quellpakete-Steuerelement
Die folgenden Modell stellt ein Beispiel für ein Steuerelement Source-Implementierung. Im Modell sehen Sie die Schnittstellen, die Sie implementieren müssen, und die Umgebung-Dienste, die Sie aufrufen müssen. Wie alle Dienste rufen Sie tatsächlich auf die Methoden der einer bestimmten Schnittstelle, die Sie über den Dienst zu erhalten. Die Namen der Klassen werden identifiziert, damit sie einfacher sehen, wie Datenquellen-Steuerelements durchgeführt wird.  
  
 ![SCC &#95; Beispiele für die TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Beispiel-Quellcodeverwaltungsprojekt  
  
## <a name="interfaces"></a>Schnittstellen  
 Sie können für Ihre neue Projekttypen in Visual Studio mit der Liste der Schnittstellen, die in der folgenden Tabelle aufgeführten Datenquellen-Steuerelements implementieren.  
  
|Schnittstelle|Verwendung|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wird von Projekten und Editoren, bevor Sie sie speichern oder ändern ("dirty")-Dateien. Diese Schnittstelle erfolgt mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Aufgerufen von Projekten, zum Anfordern von Berechtigungen zum Hinzufügen, entfernen Sie oder Umbenennen Sie einer Datei oder eines Verzeichnisses. Diese Schnittstelle wird auch aufgerufen, Projekte zu informieren, dass die Umgebung, wenn ein genehmigten hinzufügen, entfernen oder Umbenennen von Aktion abgeschlossen ist. Wird darauf mit der <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> Dienst.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Durch jede Entität, die registriert wird, um benachrichtigt zu werden, wenn Projekte hinzufügen, umbenennen oder einer Datei oder eines Verzeichnisses entfernen implementiert. Rufen Sie zum Registrieren für die ereignisbenachrichtigung <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wird von Projekten, zum Registrieren bei das Quellcodeverwaltungspaket und zum Abrufen von Informationen zum Status des Datenquellen-Steuerelement aufgerufen. Diese Schnittstelle erfolgt mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementiert das Projekt so reagieren Sie auf der Quelle steueranforderungen Informationen zu Dateien und beim Abrufen der Quelle Steuerung von Einstellungen für die Projektdatei erforderlich.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
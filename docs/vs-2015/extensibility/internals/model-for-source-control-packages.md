---
title: Modell für Quellcodeverwaltungspakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27bac56b862d4a3dfd0495420ee20920801faaae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734131"
---
# <a name="model-for-source-control-packages"></a>Modell für Quellcodeverwaltungspakete
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das folgende Modell stellt ein Beispiel für eine Source-Control-Implementierung dar. Im Modell sehen Sie die Schnittstellen, die Sie implementieren müssen, und die umgebungsdienste, die aufgerufen werden muss. Wie alle Dienste rufen Sie tatsächlich die Methoden der einer bestimmten Schnittstelle, die Sie über den Dienst zu erhalten. Die Namen der Klassen werden identifiziert, damit leichter das finden Sie unter wie Datenquellen-Steuerelement ausgeführt wird.  
  
 ![SCC&#95;KRIPT Beispiele](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Beispiel für Quellcodeverwaltungs-Projekt  
  
## <a name="interfaces"></a>Schnittstellen  
 Sie können Datenquellen-Steuerelement implementieren, für Ihre neue Projekttypen in Visual Studio mit der Liste der Schnittstellen, die in der folgenden Tabelle gezeigt.  
  
|Interface|Mit|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wird von Projekten und Editoren ein, bevor Sie sie speichern oder Änderung (geändert)-Dateien. Diese Schnittstelle erfolgt mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wird von Projekten für eine Berechtigung zum Hinzufügen, entfernen oder Umbenennen einer Datei oder eines Verzeichnisses aufgerufen. Diese Schnittstelle wird auch von Projekten aufgerufen, zu informieren, dass die Umgebung aus, wenn eine genehmigte hinzufügen, entfernen oder Umbenennen der Aktion abgeschlossen ist. Erfolgt mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> Service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Durch jede Entität, die registriert wird, um benachrichtigt zu werden, wenn Projekte hinzufügen, umbenennen oder einer Datei oder eines Verzeichnisses entfernen implementiert. Rufen Sie zum Registrieren für die ereignisbenachrichtigung <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wird von Projekten, zum Registrieren bei das Quellcodeverwaltungspaket und zum Abrufen von Informationen über Quellcodeverwaltungsstatus aufgerufen. Diese Schnittstelle erfolgt mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementiert das Projekt zum Reagieren auf Anforderungen von Datenquellen-Steuerelement für Informationen zu Dateien und beim Abrufen der Quelle verwaltungseinstellungen, die für die Projektdatei erforderlich.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)


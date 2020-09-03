---
title: VSPackage-Struktur (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205996"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Quell Code Verwaltungspaket-SDK enthält Richtlinien für das Erstellen eines VSPackages, das es einem Quellcodeverwaltungs-Implementierer ermöglicht, seine Funktionen der Quell Code Verwaltung in die Umgebung zu integrieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ein VSPackage ist eine COM-Komponente, die in der Regel von der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) basierend auf den Diensten, die vom Paket in Ihren Registrierungs Einträgen angekündigt werden, Bedarfs gesteuert geladen wird. Jedes VSPackage muss implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Ein VSPackage nutzt normalerweise Dienste, die von der IDE angeboten werden, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und stellt einige Dienste bereit.  
  
 Ein VSPackage deklariert seine Menü Elemente und legt einen Standardelement Zustand über die vsct-Datei fest. Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE zeigt die Menü Elemente in diesem Zustand an, bis das VSPackage geladen wurde. Anschließend wird die VSPackage-Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aufgerufen, um Menü Elemente zu aktivieren oder zu deaktivieren.  
  
## <a name="source-control-package-characteristics"></a>Merkmale der Quell Code Verwaltungs Pakete  
 Ein Quellcodeverwaltungs-VSPackage ist tief in integriert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Die VSPackage-Semantik umfasst Folgendes:  
  
- Schnittstelle, die durch das VSPackage implementiert werden soll (die- `IVsPackage` Schnittstelle)  
  
- Implementierung von UI-Befehlen (vsct-Datei und Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle)  
  
- Die Registrierung des VSPackage mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  Das VSPackage der Quell Code Verwaltung muss mit diesen anderen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Entitäten kommunizieren:  
  
- Projekte  
  
- Editoren  
  
- Lösungen  
  
- Windows  
  
- Die laufende Dokument Tabelle  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Möglicherweise genutzte Visual Studio-Umgebungs Dienste  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Svsregisterscciprovider-Dienst  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Implementierte und aufgerufene VSIP-Schnittstellen  
 Ein Quell Code Verwaltungspaket ist ein VSPackage und kann daher direkt mit anderen VSPackages interagieren, die bei registriert sind [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Um die vollständige Palette der Funktionen der Quell Code Verwaltung bereitzustellen, kann ein Quellcodeverwaltungs-VSPackage mit Schnittstellen arbeiten, die von Projekten oder der Shell bereitgestellt werden.  
  
 Jedes Projekt in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] muss die implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> , um als Projekt innerhalb der IDE erkannt zu werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Diese Schnittstelle ist jedoch nicht für die Quell Code Verwaltung spezialisiert. Projekte, die in der Quell Code Verwaltung erwartet werden, implementieren das-Element <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Diese Schnittstelle wird von der Quellcodeverwaltungs-VSPackage verwendet, um ein Projekt nach seinem Inhalt abzufragen und um ihm Symbole und Bindungs Informationen (die Informationen, die zum Herstellen einer Verbindung zwischen dem Serverstandort und dem Speicherort eines Projekts, das der Quell Code Verwaltung unterliegt) bereitzustellen.  
  
 Das VSPackage der Quell Code Verwaltung implementiert den <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , der wiederum es Projekten ermöglicht, sich selbst für die Quell Code Verwaltung zu registrieren und seine Statussymbole abzurufen.  
  
 Eine vollständige Liste der Schnittstellen, die von einem Quellcodeverwaltungs-VSPackage berücksichtigt werden müssen, finden Sie unter [verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Design Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

---
title: Übersicht über Lösungen mit | Microsoft-Dokumentation
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
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8204dcfc7a0d8937551914ebedbc035767127507
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292659"
---
# <a name="solutions-overview"></a>Übersicht über Projektmappen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Lösung ist eine Gruppierung von ein oder mehrere Projekte, die zum Erstellen einer Anwendung zusammenarbeiten. Projekt- und Status Informationen zu der Projektmappe werden in zwei verschiedenen Projektmappendateien gespeichert. Die Projektmappendatei (.sln) textbasiert ist und unter quellcodeverwaltung gestellt und von Benutzern gemeinsam genutzt werden können. Die Lösung Benutzer-Optionsdatei (.suo) ist binär. Daher wird die SUO-Datei kann nicht unter quellcodeverwaltung platziert werden und benutzerspezifische Informationen enthält.  
  
 Jedem VSPackage kann in beide Arten von Projektmappendatei schreiben. Aufgrund der Natur der Dateien es gibt zwei unterschiedliche Schnittstellen implementiert, um in diese schreiben. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle schreibt Textinformationen in der SLN-Datei und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> Schnittstelle binäre Datenströmen in der SUO-Datei geschrieben.  
  
> [!NOTE]
>  Ein Projekt muss nicht explizit Schreiben eines Eintrags für sich selbst in die Projektmappendatei; die Umgebung, die für das Projekt behandelt werden. Aus diesem Grund, es sei denn, Sie speziell für die Projektmappendatei Weitere Inhalte hinzufügen möchten, nicht müssen Sie das VSPackage auf diese Weise zu registrieren.  
  
 Jedes VSPackage Unterstützung der Persistenz der Lösung verwendet drei Schnittstellen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> -Schnittstelle, die von der Umgebung implementiert und vom VSPackage aufgerufen, und `IVsPersistSolutionProps` und `IVsPersistSolutionOpts`, sind beide implementiert vom VSPackage. Die `IVsPersistSolutionOpts` Schnittstelle nur implementiert werden, wenn private Informationen vom VSPackage in der SUO-Datei geschrieben werden muss.  
  
 Wenn eine Projektmappe geöffnet ist, findet der folgende Prozess statt.  
  
1.  Die Umgebung liest die Lösung.  
  
2.  Wenn die Umgebung sucht nach einer `CLSID`, lädt er die entsprechenden VSPackage.  
  
3.  Wenn eine VSPackage geladen wurde, ist die Umgebung ruft `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Schnittstelle, für die Schnittstelle, die das VSPackage ist erforderlich.  
  
    1.  Wenn von einer sln-Datei lesen, um die Umgebung ruft `QueryInterface` für `IVsPersistSolutionProps`.  
  
    2.  Wenn Sie aus einer SUO-Datei zu lesen, um die Umgebung ruft `QueryInterface` für `IVsPersistSolutionOpts`.  
  
 Spezifische Informationen im Zusammenhang mit der Verwendung dieser Dateien finden Sie in [Lösung (. Sln) Datei](../../extensibility/internals/solution-dot-sln-file.md) und [Benutzeroptionen bei Projektmappen (. Suo)-Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Wenn Sie eine neue Projektmappenkonfiguration bestehend aus zwei Projekten Konfigurationen und Ausschließen von einer dritten aus dem Build erstellen möchten, müssen Sie die Seiten-UI-Eigenschaft oder die Automatisierung zu verwenden. Sie nicht der Projektmappenbuild-Konfigurationen-Manager und deren Eigenschaften direkt ändern, aber Sie können mithilfe der projektmappenbuildmanager Bearbeiten der `SolutionBuild` Klasse von DTE im Automatisierungsmodell. Weitere Informationen zum Konfigurieren von Lösungen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>


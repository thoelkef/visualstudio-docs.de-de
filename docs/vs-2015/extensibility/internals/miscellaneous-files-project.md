---
title: Projekt "Sonstige Dateien" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179788"
---
# <a name="miscellaneous-files-project"></a>Verschiedene Projektdateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Benutzer die Projektelemente geöffnet wird, weist die IDE alle Elemente, die keine Projekte in einer Projektmappe gehören, auf das Projekt verschiedene Dateien.  
  
 Projekte spielen eine bedeutende Rolle beim bestimmen, welcher Editor verwendet wird, wenn ein Benutzer ein Projektelement geöffnet wird. Ein Projekt kann entworfen werden, um bestimmte Dateien über einen projektspezifischen Editor oder einem standard-Editor zu öffnen.  
  
 Ein projektspezifischer Editor erfordert in der Regel an, dass der Benutzer verfügen über spezielle Kenntnisse oder spezielle Schnittstellen aus dem Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Ein standard-Editor, kann in jedem Projekt eine Datei eine bestimmte Erweiterung öffnen. Benutzer kann einige standard-Editoren, anpassen, wie z. B. die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Text-Editor für Projekte, behalten aber immer noch ihre öffentlichen Zeichen. Standard-Editoren werden erstellt, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode.  
  
 Wenn kein Projekt in der Projektmappe antwortet, dass ein Projektelement geöffnet werden kann, bietet die IDE ein bestimmtes Projekt aufgerufen, das Projekt verschiedene Dateien, das eine beliebige Datei geöffnet wird.  
  
 Dieses spezielle Projekt bietet zum Öffnen einer Datei außerhalb des Kontexts eines Projekts. Bei der Verarbeitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> -Methode, mit sehr niedriger Priorität immer das Projekt verschiedene Dateien antwortet. Aus diesem Grund Projekt verschiedene Dateien immer führt zu höherer Priorität Projekte, die Dateien öffnen können.  
  
 Das Projekt verschiedene Dateien nicht, dass der Benutzer explizit erstellen sie mit der **neues Projekt** Dialogfeld. Darüber hinaus verwaltet das Projekt verschiedene Dateien nicht dauerhaft eine Liste von Projektmitgliedern. Ein optionales Feature verwendet, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufgezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)   
 [Vorgehensweise: Open-Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

---
title: Projekt verschiedene Dateien | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a637b37590a0aaf321a4e04896b2cbe12c29691f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="miscellaneous-files-project"></a>Projekt verschiedene Dateien
Wenn ein Benutzer Projektelemente geöffnet wird, weist die IDE dem Projekt verschiedene Dateien alle Elemente, die keine Mitglieder für alle Projekte in einer Projektmappe sind.  
  
 Projekte spielen eine wichtige Rolle bei der Bestimmung, welche-Editor verwendet wird, wenn ein Benutzer ein Projektelement öffnet. Ein Projekt kann entworfen werden, um bestimmte Dateien mithilfe einer projektspezifische oder standard-Editor zu öffnen.  
  
 Ein Editor projektspezifische erfordert in der Regel an, dass der Benutzer über spezielle Kenntnisse verfügen, oder verwenden Sie spezielle Schnittstellen aus dem Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen projektspezifische Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Eine standard-Editors kann in jedem Projekt eine Datei mit einer bestimmten Erweiterung öffnen. Die Benutzer kann einige standard-Editoren, anpassen, wie z. B. die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text-Editor für Projekte, behalten aber weiterhin ihre öffentliche Zeichen. Standard-Editoren werden erstellt, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode.  
  
 Wenn kein Projekt in der Projektmappe antwortet, ein Projektelement geöffnet werden kann, enthält die IDE bei ein spezielles Projekt mit das Projekt verschiedene Dateien, das eine Datei geöffnet wird.  
  
 Dieses spezielle Projekt stellt zum Öffnen einer Datei außerhalb des Kontexts eines Projekts. Bei der Verarbeitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> -Methode, mit einer sehr niedrigen Priorität immer das Projekt verschiedene Dateien antwortet. Aus diesem Grund Projekt verschiedene Dateien immer ergibt eine höhere Priorität-Projekt, die Dateien öffnen können.  
  
 Das Projekt verschiedene Dateien erfordert keine den Benutzer explizit erstellen sie mit der **neues Projekt** (Dialogfeld). Darüber hinaus verwaltet das Projekt verschiedene Dateien nicht dauerhaft eine Liste von Mitgliedern. Es verwendet ein optionales Feature, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer zu erfassen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Vorgehensweise: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md)   
 [Vorgehensweise: Öffnen Sie die Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
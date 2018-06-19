---
title: Priorität Projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27341f78fb17fa5346a9dfbc7cdd3f86439d3d23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130879"
---
# <a name="project-priority"></a>Projektpriorität
Ein Projektelement ist in der Regel Mitglied nur ein Projekt in der Projektmappe. Aus diesem Grund kann die IDE einfach bestimmen, welches Projekt verwendet wird, um das Element zu öffnen. Wenn ein Element Mitglied von mehr als ein Projekt ist, verwendet die IDE ein Prioritätsschema jedoch um das beste Projekt für das Öffnen des Elements zu ermitteln.  
  
 Die folgende Liste enthält das Schema der Projekt-Priorität:  
  
-   Ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> Methode für jedes Projekt in der Projektmappe, um zu bestimmen, ob das Dokument ein Mitglied dieses Projekt ist.  
  
-   Das Dokument ein Element des Projekts ist, antwortet das Projekt mit einer Priorität, dass das Projekt nach seiner Verarbeitung dieses Dokuments weist. Z. B. eine Sprachprojekt mit hoher Priorität für die Sprache Quelldateien reagiert jedoch antwortet mit einer niedrigeren Priorität für ein nicht erkannter Dateityp, der nicht als Teil seiner Buildprozesses verwendet wird.  
  
-   Projekte, die benutzerdefinierte, projektspezifische Editoren oder Designer für ein Dokument Bereitstellen erhalten außerdem einen hohen Stellenwert.  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration enthält das Dokument Priority-Werte.  
  
-   Das Projekt, das angibt, die höchste Priorität erhält den Kontext, um das Dokument zu öffnen. Wenn zwei Projekte gleich Priority-Werte zurückgegeben, wird das aktive Projekt bevorzugt. Wenn kein Projekt in der Projektmappe antwortet, das Dokument geöffnet werden kann, setzt die IDE das Dokument im Projekt verschiedene Dateien. Weitere Informationen finden Sie unter [sonstige Dateiprojekt](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Projekt verschiedene Dateien](../../extensibility/internals/miscellaneous-files-project.md)   
 [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
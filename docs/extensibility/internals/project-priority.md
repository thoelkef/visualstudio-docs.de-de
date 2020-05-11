---
title: Projektpriorität | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706419"
---
# <a name="project-priority"></a>Projektpriorität
Ein Projektelement ist in der Regel nur Mitglied eines Projekts in der Projektmappe. Daher kann die IDE leicht bestimmen, welches Projekt zum Öffnen des Elements verwendet wird. Wenn ein Element jedoch Mitglied mehrerer Projekte ist, verwendet die IDE ein Prioritätsschema, um das beste Projekt zum Öffnen des Elements zu ermitteln.

 Die folgende Liste zeigt das Projektprioritätsschema:

- Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> ruft die Methode für jedes Projekt in der Projektmappe auf, um zu bestimmen, ob das Dokument Mitglied dieses Projekts ist.

- Wenn das Dokument Mitglied des Projekts ist, antwortet das Projekt mit einer Priorität, die das Projekt entsprechend der Behandlung dieses Dokuments zuweist. Beispielsweise antwortet ein Sprachprojekt mit hoher Priorität für seine Sprachquelldateien, aber mit einer niedrigeren Priorität für einen nicht erkannten Dateityp, der nicht als Teil des Buildprozesses verwendet wird.

- Projekte, die benutzerdefinierte, projektspezifische Editoren oder Designer für ein Dokument bereitstellen, erhalten ebenfalls eine hohe Priorität.

- Die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration stellt die Dokumentprioritätswerte bereit.

- Dem Projekt, das die höchste Priorität angibt, wird der Kontext zum Öffnen des Dokuments angegeben. Wenn zwei Projekte gleiche Prioritätswerte zurückgeben, wird das aktive Projekt bevorzugt. Wenn kein Projekt in der Projektmappe darauf antwortet, dass es das Dokument öffnen kann, legt die IDE das Dokument im Projekt Verschiedene Dateien ab. Weitere Informationen finden Sie unter [Projekt für verschiedene Dateien](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Weitere Informationen
- [Verschiedene Projektdateien](../../extensibility/internals/miscellaneous-files-project.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

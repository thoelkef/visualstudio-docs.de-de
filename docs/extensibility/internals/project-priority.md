---
title: Projekt Priorität | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706419"
---
# <a name="project-priority"></a>Projektpriorität
Ein Projekt Element ist in der Regel ein Member von nur einem Projekt in der Projekt Mappe. Aus diesem Grund kann die IDE leicht feststellen, welches Projekt zum Öffnen des Elements verwendet wird. Wenn ein Element jedoch Mitglied von mehr als einem Projekt ist, verwendet die IDE ein Prioritäts Schema, um das beste Projekt für das Öffnen des Elements zu bestimmen.

 In der folgenden Liste wird das Projekt Prioritäts Schema angezeigt:

- Die IDE Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> Methode für jedes Projekt in der Projekt Mappe auf, um zu bestimmen, ob das Dokument ein Member dieses Projekts ist.

- Wenn das Dokument ein Member des Projekts ist, antwortet das Projekt mit einer Priorität, die das Projekt entsprechend seiner Behandlung dieses Dokuments zuweist. Ein Sprachprojekt antwortet z. b. mit einer hohen Priorität für seine sprach Quelldateien, antwortet aber mit niedrigerer Priorität für einen nicht erkannten Dateityp, der nicht als Teil des Buildprozesses verwendet wird.

- Projekte, die benutzerdefinierte, projektspezifische Editoren oder Designer für ein Dokument bereitstellen, erhalten ebenfalls eine hohe Priorität.

- Die- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration stellt die Werte für die Dokument Priorität bereit.

- Das Projekt, das die höchste Priorität angibt, erhält den Kontext, um das Dokument zu öffnen. Wenn zwei Projekte die gleichen Prioritätswerte zurückgeben, wird das aktive Projekt bevorzugt. Wenn kein Projekt in der Projekt Mappe antwortet, dass das Dokument geöffnet werden kann, fügt die IDE das Dokument in das Projekt "sonstige Dateien" ein. Weitere Informationen finden Sie unter [Projekt "sonstige Dateien](../../extensibility/internals/miscellaneous-files-project.md)".

## <a name="see-also"></a>Weitere Informationen
- [Verschiedene Projektdateien](../../extensibility/internals/miscellaneous-files-project.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

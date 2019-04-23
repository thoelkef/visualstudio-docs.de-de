---
title: Projekt Priorität | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d444896c305130c7805b8fd6ec1bdf020ed446d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089444"
---
# <a name="project-priority"></a>Projektpriorität
Ein Projektelement ist in der Regel ein Element nur ein Projekt in der Projektmappe. Aus diesem Grund kann die IDE einfach bestimmen, welches Projekt verwendet wird, um das Element zu öffnen. Wenn ein Element ein Mitglied von mehr als ein Projekt ist, verwendet die IDE ein Prioritätsschema jedoch um das beste-Projekt für das Öffnen des Elements zu bestimmen.

 Die folgende Liste enthält das Schema der Projekt-Priorität:

- Die IDE-Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> Methode für jedes Projekt in der Lösung zu bestimmen, ob das Dokument ein Mitglied dieses Projekts ist.

- Wenn das Dokument ein Member des Projekts ist, antwortet das Projekt mit einer Priorität, dass das Projekt entsprechend die Behandlung dieses Dokument weist. Beispielsweise ein Sprachprojekt mit hoher Priorität für seine Sprache Quelldateien reagiert jedoch antwortet mit einer niedrigeren Priorität für einen unbekannten Dateityp, der als Teil der Buildprozess nicht verwendet wird.

- Projekte, die benutzerdefinierten, projektspezifische Editoren oder Designer für ein Dokument bieten erhalten eine hohe Priorität.

- Die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration stellt Werte für die Failoverpriorität des Dokuments bereit.

- Das Projekt, das angibt, die höchste Priorität erhält den Kontext, der das Dokument zu öffnen. Wenn zwei Projekte gleich Priority-Werte zurückgeben, wird das aktive Projekt bevorzugt. Wenn kein Projekt in der Projektmappe antwortet, dass das Dokument geöffnet werden kann, fügt die IDE das Dokument im Projekt verschiedene Dateien. Weitere Informationen finden Sie unter [Projekt "Sonstige Dateien"](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Siehe auch
- [Verschiedene Projektdateien](../../extensibility/internals/miscellaneous-files-project.md)
- [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
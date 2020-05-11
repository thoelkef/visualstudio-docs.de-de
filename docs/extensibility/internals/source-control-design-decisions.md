---
title: Entscheidungen zur Quellcodeverwaltung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705247"
---
# <a name="source-control-design-decisions"></a>Entwurfsentscheidungen bei der Quellcodeverwaltung
Die folgenden Entwurfsentscheidungen sollten bei der Implementierung der Quellcodeverwaltung für Projekte berücksichtigt werden.

## <a name="will-information-be-shared-or-private"></a>Werden Informationen geteilt oder privat?
 Die wichtigste Designentscheidung, die Sie treffen können, ist, welche Informationen sharable und was privat ist. Beispielsweise wird die Liste der Dateien für das Projekt freigegeben, aber in dieser Liste von Dateien möchten einige Benutzer möglicherweise private Dateien haben. Compilereinstellungen werden gemeinsam genutzt, aber das Startprojekt ist im Allgemeinen privat. Einstellungen werden entweder rein gemeinsam genutzt, mit einer Außerkraftsetzung geteilt oder rein privat. Private Elemente, z. B. Lösungsbenutzeroptionen (.suo)-Dateien, werden standardmäßig nicht in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]eingecheckt. Achten Sie darauf, alle privaten Informationen in privaten Dateien zu speichern, z. B. in der .suo-Datei oder in einer bestimmten privaten Datei, die Sie erstellen, z. B. eine .csproj.user-Datei für Visual C oder eine .vbproj.user-Datei für Visual Basic.

 Diese Entscheidung ist nicht allumfassend und kann artikelweise getroffen werden.

## <a name="will-the-project-include-special-files"></a>Enthält das Projekt spezielle Dateien?
 Eine weitere wichtige Entwurfsentscheidung ist, ob Ihre Projektstruktur spezielle Dateien verwendet. Spezielle Dateien sind ausgeblendete Dateien, die den Dateien zugrunde liegen, die im Projektmappen-Explorer und in den Dialogfeldern Ein- und Auschecken sichtbar sind. Wenn Sie spezielle Dateien verwenden, befolgen Sie die folgenden Richtlinien:

1. Ordnen Sie dem Projektstammknoten keine speziellen Dateien zu, d. h. der Projektdatei selbst. Die Projektdatei muss eine einzelne Datei sein.

2. Wenn spezielle Dateien in einem Projekt hinzugefügt, entfernt <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> oder umbenannt werden, müssen die entsprechenden Ereignisse mit dem Flagsatz ausgelöst werden, der angibt, dass es sich bei den Dateien um spezielle Dateien handelt. Diese Ereignisse werden von der Umgebung als Reaktion <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> auf das Projekt aufgerufen, das die entsprechenden Methoden aufruft.

3. Wenn Ihr Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> oder Editor nach einer Datei ruft, werden die mit dieser Datei verknüpften speziellen Dateien nicht automatisch ausgecheckt. Übergeben Sie die speziellen Dateien zusammen mit der übergeordneten Datei. Die Umgebung erkennt die Beziehung zwischen allen übergebenen Dateien und blendet die speziellen Dateien in der Auscheckbenutzeroberfläche entsprechend aus.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)

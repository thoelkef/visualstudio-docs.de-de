---
title: Dialogfeld "Buildereignisse" (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38ef3b173643c7bff0e1417ffc9ecfb431b06685
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944134"
---
# <a name="build-events-dialog-box-visual-basic"></a>Dialogfeld "Buildereignisse" (Visual Basic)
Verwenden Sie das Dialogfeld **Buildereignisse**, um die Anweisungen für die Buildkonfiguration festzulegen. Außerdem können Sie die Bedingungen angeben, unter denen sämtliche Präbuild- und Postbuildereignisse ausgeführt werden sollen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Befehlszeile für Präbuildereignis:** Gibt sämtliche Befehle an, die vor dem Buildvorgang ausgeführt werden sollen. Klicken Sie auf **Präbuild bearbeiten...**, um das [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) anzuzeigen. In dieses Feld können Sie lange Befehle eingeben.

> [!NOTE]
> Präbuildereignisse werden nicht ausgeführt, wenn das Projekt auf dem neuesten Stand ist, und es wird kein Buildvorgang gestartet.


 **Befehlszeile für Postbuildereignis:** Gibt sämtliche Befehle an, die nach dem Buildvorgang ausgeführt werden sollen. Klicken Sie auf **Postbuild bearbeiten**, um das **Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“** anzuzeigen. In dieses Feld können Sie lange Befehle eingeben.

> [!NOTE]
> Fügen Sie allen Postbuildbefehlen, die BAT-Dateien ausführen, eine `call`-Anweisung hinzu. Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Postbuildereignis ausführen:** Gibt die Bedingungen für das auszuführende Postbuildereignis an. Diese werden in der folgenden Tabelle dargestellt.

|Option|Ergebnis|
|------------|------------|
|**Immer**|Das Postbuildereignis wird ausgeführt, unabhängig davon, ob der Buildvorgang erfolgreich ist.|
|**Bei erfolgreichem Erstellen**|Das Postbuildereignis wird ausgeführt, wenn der Buildvorgang erfolgreich ist. Das Ereignis wird sogar für ein aktuelles Projekt ausgeführt, solange der Buildvorgang erfolgreich ist. Dies ist die Standardeinstellung.|
|**Wenn der Build die Projektausgabe aktualisiert**|Das Postbuildereignis wird nur ausgeführt, wenn sich die Ausgabedatei des Compilers (.exe or .dll) von der vorherigen Ausgabedatei des Compilers unterscheidet. Es wird kein Postbuildereignis ausgeführt, wenn das Projekt aktuell ist.|

## <a name="see-also"></a>Siehe auch

- [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Gewusst wie: Festlegen von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
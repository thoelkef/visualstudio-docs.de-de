---
title: Optionen, Text-Editor, HTML (Web Forms), Validierung
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f629a0b8d9f149ee10f7a35c75e351a6c3abfd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031772"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Optionen, Text-Editor, HTML (Web Forms), Validierung

Verwenden Sie die Optionsseite **Validierung**, um festlegen, wie der HTML-Editor die Syntax von HTML-Markup im Dokument überprüft. Öffnen Sie diese Seite, indem Sie auf der Menüleiste auf **Tools** > **Optionen** klicken und anschließend **Text-Editor** > **HTML (Web Forms)** > **Validierung** erweitern.

## <a name="validation"></a>Validierung

- **Doctype zur Validierungsschemaerkennung verwenden**

   Ein Schema bestimmt, welche Elemente, Attribute und Schreibweise für das Schema gültig sind. Es bestimmt außerdem die Tags und Attribute, die in IntelliSense verfügbar sind.

   Wählen Sie diese Option aus, wenn Visual Studio den Inhalt der **<!DOCTYPE>**-Deklaration und des **html**-Elements der Seite verwenden soll, um das Schema zu bestimmen. Wenn Sie diese Option aktivieren und die Seite die Deklaration `<!DOCTYPE html>` enthält, verwendet Visual Studio das Schema HTML5. Wenn das **html**-Tag jedoch ein **xmlns**-Attribut aufweist, wie beispielsweise `<html xmlns="http://www.w3.org/1999/xhtml">`, verwendet Visual Studio das Schema XHTML5.

- **Ziel bei nicht gefundenem Doctype**

   Wählen Sie das Schema für die Überprüfung aus, wenn keine **<!DOCTYPE>**-Deklaration auf der Seite vorhanden ist.

  - **Fehler anzeigen**

     Wählen Sie das Kontrollkästchen aus, um die Validierung zu aktivieren. Wenn das Kontrollkästchen nicht aktiviert ist, markiert der Editor keine Validierungsfehler.

     Mit den anderen Kontrollkästchen können Sie die Validierung weiter verfeinern, indem Sie einzelne Fehlertypen angeben, die im Editor markiert werden sollen.

     > [!NOTE]
     > Einige Schemas bieten nicht die Option zur Markierung einzelner Fehlertypen. Wenn Sie beispielsweise als Zielschema **XHTML 1.1** auswählen, werden alle optionalen Kontrollkästchen deaktiviert. In diesem Fall werden alle Fehlertypen markiert.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
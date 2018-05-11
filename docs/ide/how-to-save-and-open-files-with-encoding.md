---
title: 'Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6298e603589d41a6a082b6fe2c1916b3cf8a2a84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung

Sie können Dateien mit ausgewählter Zeichencodierung speichern, sodass bidirektionale Sprachen unterstützt werden. Sie können außerdem auch beim Öffnen einer Datei eine Codierung angeben, sodass Visual Studio die Datei korrekt anzeigt.

## <a name="to-save-a-file-with-encoding"></a>So speichern Sie eine codierte Datei

1.  Klicken Sie im Menü **Datei** auf **Datei speichern unter**, und klicken Sie dann neben der Schaltfläche **Speichern** auf die Dropdownschaltfläche.

     Das Dialogfeld **Erweiterte Speicheroptionen** wird angezeigt.

2.  Wählen Sie unter **Codierung** die gewünschte Codierung für diese Datei aus.

3.  Optional können Sie unter **Zeilenenden** das Format für die Zeichen am Zeilenende auswählen.

     Diese Option ist sehr praktisch, wenn Sie die Datei an Benutzer eines anderen Betriebssystems weitergeben möchten.

     Wenn Sie mit einer Datei arbeiten möchten, von der Sie wissen, wie sie codiert wurde, können Sie in Visual Studio angeben, dass diese Codierung beim Öffnen verwendet werden soll. Welche Methode Sie verwenden, hängt davon ab, ob die Datei Teil des Projekts ist.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>So öffnen Sie eine codierte Datei, die Teil eines Projekts ist

1.  Klicken Sie im **Projektmappen**-Explorer mit der rechten Maustaste auf die Datei, und wählen Sie **Öffnen mit** aus.

2.  Wählen Sie im Dialogfeld **Öffnen mit** den Editor aus, mit dem die Datei geöffnet werden soll.

     Viele der Editoren von Visual Studio, z. B. der Formular-Editor, erkennen die Codierung automatisch und öffnen die Datei dann entsprechend. Wenn Sie einen Editor verwenden, bei dem Sie eine Codierung auswählen können, wird das Dialogfeld **Codierung** angezeigt.

3.  Wählen Sie in diesem Fall im Dialogfeld **Codierung** die vom Editor zu verwendende Codierung aus.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>So öffnen Sie eine codierte Datei, die nicht Teil eines Projekts ist

1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, wählen Sie **Datei** oder **Datei im Web** aus, und wählen Sie dann die zu öffnende Datei aus.

2.  Klicken Sie neben der Schaltfläche **Öffnen** auf die Dropdownschaltfläche, und klicken Sie auf **Öffnen mit**.

3.  Führen Sie die Schritte 2 und 3 der vorherigen Prozedur aus.

## <a name="see-also"></a>Siehe auch

- [Codierungen und Zeilenumbrüche](encodings-and-line-breaks.md)
- [Codierung und die Globalisierung von Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
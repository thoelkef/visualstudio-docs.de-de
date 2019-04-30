---
title: 'Vorgehensweise: Bearbeiten von XML-Dateien'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840368"
---
# <a name="how-to-edit-xml-files"></a>Vorgehensweise: Bearbeiten von XML-Dateien

Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: *config*, *.dtd*, *XML*, *XSD*, *.xdr*, *.xsl*, *.xslt*, und *.vssettings*. Der XML-Editor ist auch jeder andere Dateityp, besitzt kein bestimmten Editor registriert und XML- bzw. DTD-Inhalt enthält, zugeordnet.

> [!NOTE]
> XHTML-Dokumente werden vom HTML-Editor behandelt.

Um eine XML-Datei zu bearbeiten, doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.

## <a name="add-a-new-xml-file-to-a-project"></a>Fügen Sie eine neue XML-Datei zu einem Projekt

1. Von der **Projekt** , wählen Sie im Menü **neues Element hinzufügen**.

2. Wählen Sie **XML-Datei** aus der **Vorlagen** Bereich.

3. Geben Sie den Dateinamen in der **Namen** Feld, und drücken Sie **hinzufügen**.

   Die XML-Datei wird dem Projekt hinzugefügt und wird in der XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Hinzufügen einer vorhandenen XML-Datei zu einem Projekt

1. Von der **Projekt** , wählen Sie im Menü **vorhandenes Element hinzufügen**.

   Die **vorhandenes Element hinzufügen** Dialogfeld wird angezeigt.

2. Wählen Sie eine XML-Datei, und drücken Sie **hinzufügen**.

## <a name="create-a-new-xml-or-xslt-file"></a>Erstellen Sie eine neue XML- oder XSLT-Datei

1. Von der **Datei** , wählen Sie im Menü **neu**.

   Die **neue Datei** Dialogfeld wird angezeigt.

2. Wählen Sie **XML-Datei** , erstellen eine neue XML-Datei, oder wählen Sie **XSLT-Datei** um ein neues XSLT-Stylesheet zu erstellen.

3. Klicken Sie auf **Öffnen**.

## <a name="create-an-empty-project-for-xml-files"></a>Erstellen Sie ein leeres Projekt für XML-Dateien

::: moniker range="vs-2017"

1. Von der **Datei** , wählen Sie im Menü **neu** > **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Wählen Sie die Codesprache Ihrer Wahl wählen **leeres Projekt**.

3. Klicken Sie auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Von der **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Geben Sie **leeres Projekt** wählen Sie in das Suchfeld Vorlage die **leeres Projekt ((.NET Framework)** Vorlage, und klicken Sie dann auf **Weiter**.

3. Klicken Sie auf **Erstellen**.

::: moniker-end

4. Fügen Sie dem Projekt XML-Dateien hinzu.

   Der XML-Editor sucht die Schemas, die Sie diesem Projekt hinzu und verwendet sie für die Validierung und IntelliSense-Funktionen in jeder XML-, Schema oder XSLT-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)
- [XML-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)
- [Vorgehensweise: Erstellen Sie ein XML-Schema aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
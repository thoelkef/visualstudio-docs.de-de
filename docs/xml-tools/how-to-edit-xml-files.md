---
title: 'Gewusst wie: Bearbeiten von XML-Dateien'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 216718627936ac7f519c1a6a28a30886e8ae9c27
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592736"
---
# <a name="how-to-edit-xml-files"></a>Gewusst wie: Bearbeiten von XML-Dateien

Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT*und *. vssettings*. Der XML-Editor ist auch mit einem beliebigen anderen Dateityp verknüpft, für den kein bestimmter Editor registriert ist und der XML-oder DTD-Inhalt enthält.

> [!NOTE]
> XHTML-Dokumente werden vom HTML-Editor behandelt.

Zum Bearbeiten einer XML-Datei doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.

## <a name="add-a-new-xml-file-to-a-project"></a>Hinzufügen einer neuen XML-Datei zu einem Projekt

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen**aus.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** aus.

3. Geben Sie den Dateinamen im Feld **Name** ein, und drücken **Sie hinzufügen**.

   Die XML-Datei wird dem Projekt hinzugefügt und im XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Hinzufügen einer vorhandenen XML-Datei zu einem Projekt

1. Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.

   Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.

2. Wählen Sie eine XML-Datei und dann **Hinzufügen**aus.

## <a name="create-a-new-xml-or-xslt-file"></a>Erstellen einer neuen XML-oder XSLT-Datei

1. Wählen Sie im Menü **Datei** die Option **neu**aus.

   Das Dialogfeld **Neue Datei** wird angezeigt.

2. **XML-Datei** auswählen, um eine neue XML-Datei zu erstellen. oder wählen Sie **XSLT-Datei** aus, um ein neues XSLT-Stylesheet zu erstellen.

3. Klicken Sie auf **Öffnen**.

## <a name="create-an-empty-project-for-xml-files"></a>Erstellen eines leeren Projekts für XML-Dateien

::: moniker range="vs-2017"

1. Wählen Sie im Menü **Datei** die Option **neu** > **Projekt**aus.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Wählen Sie die gewünschte Codesprache aus, und wählen Sie dann die Vorlage **leeres Projekt (.NET Framework)** aus.

3. Klicken Sie auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Menü **Datei** die Option **neu** > **Projekt**aus.

2. Geben Sie im Feld für die Vorlagen Suche ein **leeres Projekt** ein, wählen Sie die Vorlage **leeres Projekt (.NET Framework)** aus, und klicken Sie dann auf **weiter**.

3. Klicken Sie auf **Erstellen**.

::: moniker-end

4. Fügen Sie dem Projekt XML-Dateien hinzu.

   Der XML-Editor sucht die Schemas, die Sie zu diesem Projekt hinzufügen, und verwendet Sie für die Validierung und IntelliSense in beliebigen XML-, Schema-oder XSLT-Dateien, die Sie bearbeiten, während dieses Projekt geöffnet ist.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
- [XML-Dokumenteigenschaften, Eigenschaften Fenster](../xml-tools/xml-document-properties-properties-window.md)
- [Gewusst wie: Erstellen eines XML-Schemas aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)

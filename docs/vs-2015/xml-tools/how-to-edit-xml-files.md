---
title: 'Gewusst wie: Bearbeiten von XML-Dateien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670886"
---
# <a name="how-to-edit-xml-files"></a>Gewusst wie: Bearbeiten von XML-Dateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt und .vssettings. Dem XML-Editor wird auch jeder andere Dateityp mit XML- bzw. DTD-Inhalten zugeordnet, für den kein bestimmter Editor registriert ist.

> [!NOTE]
> XHTML-Dokumente werden vom HTML-Editor behandelt.

### <a name="to-edit-an-xml-file"></a>So bearbeiten Sie eine XML-Datei

1. Doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.

### <a name="to-add-a-new-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine neue XML-Datei hinzu

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen**aus.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** aus.

3. Geben Sie den Dateinamen im Feld **Name** ein, und drücken **Sie hinzufügen**.

     Die XML-Datei wird dem Projekt hinzugefügt und im XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine vorhandene XML-Datei hinzu

1. Wählen Sie im Menü **Projekt** die Option **Vorhandenes Element hinzufügen**aus.

     Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.

2. Wählen Sie eine XML-Datei und dann **Hinzufügen**aus.

### <a name="to-create-a-new-xml-or-xslt-file"></a>So erstellen Sie eine neue XML- oder XSLT-Datei

1. Wählen Sie im Menü **Datei** die Option **neu**aus.

     Das Dialogfeld **neue Datei** wird angezeigt.

2. **XML-Datei** auswählen, um eine neue XML-Datei zu erstellen. oder wählen Sie **XSLT-Datei** aus, um ein neues XSLT-Stylesheet zu erstellen.

3. Klicken Sie auf **Öffnen**.

### <a name="to-create-a-project-for-xml-files"></a>So erstellen Sie ein Projekt für XML-Dateien

1. Wählen Sie im Menü **Datei** die Option **neu**aus, und wählen Sie dann **Projekt**aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Wählen Sie die gewünschte Codesprache aus, wählen Sie **leeres Projekt**aus, und klicken Sie auf **OK**.

3. Fügen Sie dem Projekt XML-Dateien hinzu.

     Der XML-Editor sucht die dem Projekt hinzugefügten Schemata und verwendet sie für die Validierung und für IntelliSense in allen XML-, Schema- oder XSLT-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.

## <a name="see-also"></a>Siehe auch
 XML- [Editor](../xml-tools/xml-editor.md) -XML- [Dokumenteigenschaften, Eigenschaften Fenster](../xml-tools/xml-document-properties-properties-window.md) Gewusst [wie: Erstellen eines XML-Schemas aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)

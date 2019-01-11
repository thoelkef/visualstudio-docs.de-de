---
title: 'Vorgehensweise: Bearbeiten von XML-Dateien'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5fc57c894c1e3a616062f01cc46103b4714fa35
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849044"
---
# <a name="how-to-edit-xml-files"></a>Vorgehensweise: Bearbeiten von XML-Dateien

Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: *config*, *.dtd*, *XML*, *XSD*, *.xdr*, *.xsl*, *.xslt*, und *.vssettings*. Dem XML-Editor wird auch jeder andere Dateityp mit XML- bzw. DTD-Inhalten zugeordnet, für den kein bestimmter Editor registriert ist.

> [!NOTE]
> XHTML-Dokumente werden vom HTML-Editor behandelt.

## <a name="to-edit-an-xml-file"></a>So bearbeiten Sie eine XML-Datei

1.  Doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.

### <a name="to-add-a-new-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine neue XML-Datei hinzu

1.  Von der **Projekt** , wählen Sie im Menü **neues Element hinzufügen**.

2.  Wählen Sie **XML-Datei** aus der **Vorlagen** Bereich.

3.  Geben Sie den Dateinamen in der **Namen** Feld, und drücken Sie **hinzufügen**.

     Die XML-Datei wird dem Projekt hinzugefügt und im XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine vorhandene XML-Datei hinzu

1.  Von der **Projekt** , wählen Sie im Menü **vorhandenes Element hinzufügen**.

     Die **vorhandenes Element hinzufügen** Dialogfeld wird angezeigt.

2.  Wählen Sie eine XML-Datei, und drücken Sie **hinzufügen**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>So erstellen Sie eine neue XML- oder XSLT-Datei

1.  Von der **Datei** , wählen Sie im Menü **neu**.

     Die **neue Datei** Dialogfeld wird angezeigt.

2.  Wählen Sie **XML-Datei** , erstellen eine neue XML-Datei, oder wählen Sie **XSLT-Datei** um ein neues XSLT-Stylesheet zu erstellen.

3.  Klicken Sie auf **Öffnen**.

## <a name="to-create-a-project-for-xml-files"></a>So erstellen Sie ein Projekt für XML-Dateien

1.  Von der **Datei** , wählen Sie im Menü **neu**, und wählen Sie dann **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2.  Wählen Sie die Codesprache Ihrer Wahl wählen **leeres Projekt**, und klicken Sie auf **OK**.

3.  Fügen Sie dem Projekt XML-Dateien hinzu.

     Der XML-Editor sucht die dem Projekt hinzugefügten Schemata und verwendet sie für die Validierung und für IntelliSense in allen XML-, Schema- oder XSLT-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
- [XML-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)
- [Vorgehensweise: Erstellen Sie ein XML-Schema aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
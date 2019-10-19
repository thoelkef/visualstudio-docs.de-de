---
title: XML-Editor und Schema-Designer
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9412d89ee7d9ad1412f0eaf9fe9341e336a65e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668711"
---
# <a name="xml-tools-in-visual-studio"></a>XML-Tools in Visual Studio

*Extensible Markup Language (XML)* ist eine Markup Sprache, die ein Format zum Beschreiben von Daten bereitstellt. XML trennt die Daten und ihre Darstellung durch die Verwendung zugeordneter Stylesheets wie Extensible Stylesheet Language (XSL) und Cascading Stylesheets (CSS). Visual Studio enthält Tools und Funktionen, die das Arbeiten mit XML, XSLT und XML-Schemas vereinfachen.

## <a name="xml-editor"></a>XML-Editor

Der [XML-Editor](xml-editor.md) wird zum Bearbeiten von XML-Dokumenten verwendet. Sie bietet vollständige Überprüfung der XML-Syntax, Schema Validierung während der Typerstellung, Farbcodierung und IntelliSense. Wenn ein Schema oder eine DTD (Dokumenttypdefinition) bereitgestellt wird, werden von IntelliSense damit die zulässigen Elemente und Attribute aufgelistet.

Folgende zusätzlichen Funktionen sind verfügbar:

- Unterstützung von XML-Ausschnitten, einschließlich Schema generierter Ausschnitte

- Dokument Gliederung, sodass Elemente erweitert und reduziert werden können

- Die Fähigkeit zum Ausführen von XSLT-Transformationen und zum Anzeigen der Ergebnisse als Text, XML oder HTML

- Die Fähigkeit zum Generieren von XSD-Schemas (XML Schema Definition Language) aus dem XML-Instanzdokument

- Unterstützung für das Bearbeiten von XSLT-Stylesheets, einschließlich IntelliSense-Unterstützung

- XML-Schema-Explorer

## <a name="xml-schema-designer"></a>XML-Schema-Designer

Der [XML-Schema-Designer](xml-schema-designer.md) ist in Visual Studio und den XML-Editor integriert, damit Sie mit XSD-Schemas (XML Schema Definition Language) arbeiten können.

## <a name="xslt-debugging"></a>Debuggen von XSLT-Code

Visual Studio unterstützt das [Debugging von XSLT-Stylesheets](../xml-tools/debugging-xslt.md). Mithilfe des Debuggers können Sie Haltepunkte in einem XSLT-Stylesheet festlegen, den Code in einem XSLT-Stylesheet schrittweise ausführen usw.

> [!NOTE]
> Der XSLT-Debugger ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml?displayProperty=fullName>
- [XSLT-Transformationen](/dotnet/standard/data/xml/xslt-transformations)
- [Verarbeiten von XML-Daten mit dem XPath-Datenmodell](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML-Dokumentobjektmodell (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML Schema Object Model (SOM) (XML-Schemaobjektmodell (SOM))](/dotnet/standard/data/xml/xml-schema-object-model-som)
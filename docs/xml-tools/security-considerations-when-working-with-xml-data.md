---
title: Sicherheitsaspekte beim Arbeiten mit XML-Daten
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0eb38118f7e71bd8cab0cf3faf367c01700cae0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604600"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Sicherheitsüberlegungen beim Arbeiten mit XML-Daten

In diesem Thema werden Sicherheitsprobleme erläutert, die Sie bei der Arbeit mit dem XML-Editor oder dem XSLT-Debugger kennen müssen.

## <a name="xml-editor"></a>XML-Editor

Der XML-Editor basiert auf dem Visual Studio-Text-Editor. Er beruht auf der <xref:System.Xml>-Klasse und der <xref:System.Xml.Xsl>-Klasse zum Behandeln vieler XML-Prozesse.

- XSLT-Transformationen werden in einer neuen Anwendungsdomäne ausgeführt. Die XSLT-Transformationen sind *Sandkasten*. Das heißt, die Sicherheitsrichtlinie für den Code Zugriff Ihres Computers wird verwendet, um die eingeschränkten Berechtigungen basierend auf der Position des XSLT-Stylesheets zu bestimmen. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse wird XSLT in die Microsoft Intermediate Language (MSIL) kompiliert, um eine höhere Leistung bei der Ausführung zu erzielen.

- Schemas, die auf einen externen Speicherort in der Katalog Datei verweisen, werden beim ersten Laden des XML-Editors automatisch heruntergeladen. Mithilfe der <xref:System.Xml.Schema.XmlSchemaSet>-Klasse werden Schemata kompiliert. Die Katalog Datei, die mit dem XML-Editor ausgeliefert wird, enthält keine Links zu externen Schemas. Der Benutzer muss explizit einen Verweis auf das externe Schema hinzufügen, bevor der XML-Editor die Schema Datei herunterlädt. Das Herunterladen von http kann über die **Options Seite verschiedene Tools** für den XML-Editor deaktiviert werden.

- Der XML-Editor verwendet die <xref:System.Net> Klassen zum Herunterladen von Schemas.

## <a name="xslt-debugger"></a>XSLT-Debugger

Der XSLT-Debugger verwendet aus Visual Studio die verwaltete Debug-Engine und die verwalteten Klassen aus dem <xref:System.Xml>-Namespace und dem <xref:System.Xml.Xsl>-Namespace.

- Der XSLT-Debugger führt jede XSLT-Transformation in einer Sandbox-Anwendungsdomäne aus. Mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers werden die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets ermittelt. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Das XSLT-Stylesheet wird mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse kompiliert.

- Die XSLT-Ausdrucksauswertung wird von der verwalteten Debug-Engine geladen. Die verwaltete Debug-Engine geht davon aus, dass der gesamte Code auf dem lokalen Computer des Benutzers ausgeführt wird. Daher lädt die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT-Datei auf den lokalen Computer des Benutzers. Die Möglichkeit einer Anhebung der Ausführungsberechtigung wird dadurch minimiert, dass alle XSLT-Transformationen in einer neuen Anwendungsdomäne mit eingeschränkten Berechtigungen ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Anwendungsdomänen](/dotnet/framework/app-domains/application-domains)
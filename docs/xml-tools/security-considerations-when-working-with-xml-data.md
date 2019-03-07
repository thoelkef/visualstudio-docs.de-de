---
title: Sicherheitsaspekte beim Arbeiten mit XML-Daten
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3af91f02b6cc34fcc05b83bb6c09cfd37e8a18ef
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525465"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Überlegungen zur Sicherheit bei der Arbeit mit XML-Daten

Dieses Thema beschreibt die Sicherheitsprobleme, denen Sie beim Arbeiten mit XML-Editor oder dem XSLT-Debugger kennen müssen.

## <a name="xml-editor"></a>XML-editor

 Der XML-Editor basiert auf der Visual Studio-Text-Editor. Er beruht auf der <xref:System.Xml>-Klasse und der <xref:System.Xml.Xsl>-Klasse zum Behandeln vieler XML-Prozesse.

-   XSLT-Transformationen werden in einer neuen Anwendungsdomäne ausgeführt. Die XSLT-Transformationen sind *Sandbox*; also wird die Sicherheitsrichtlinie für Codezugriff Ihres Computers verwendet, um zu bestimmen, die eingeschränkten Berechtigungen, die basierend auf, in dem das XSLT-Stylesheet befindet. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

-   Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse wird XSLT in die Microsoft Intermediate Language (MSIL) kompiliert, um eine höhere Leistung bei der Ausführung zu erzielen.

-   Schemas, die auf einem externen Speicherort in der Katalogdatei zeigen, werden automatisch heruntergeladen, beim ersten Laden der XML-Editor. Mithilfe der <xref:System.Xml.Schema.XmlSchemaSet>-Klasse werden Schemata kompiliert. Links zu externen Schemata keinen für die Katalogdatei, die im XML-Editor bereitgestellt wird. Der Benutzer hat einen Verweis auf das externe Schema explizit hinzufügen, bevor der XML-Editor die Schemadatei herunterlädt. HTTP-Downloads kann deaktiviert werden, über die **verschiedene Extras/Optionen** Seite für den XML-Editor.

-   Der XML-Editor verwendet die <xref:System.Net> Klassen für Downloads von Schemata

## <a name="xslt-debugger"></a>XSLT-Debugger

 Der XSLT-Debugger verwendet aus Visual Studio die verwaltete Debug-Engine und die verwalteten Klassen aus dem <xref:System.Xml>-Namespace und dem <xref:System.Xml.Xsl>-Namespace.

-   Der XSLT-Debugger führt jede XSLT-Transformation in einer Sandbox-Anwendungsdomäne aus. Mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers werden die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets ermittelt. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

-   Das XSLT-Stylesheet wird mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse kompiliert.

-   Die XSLT-Ausdrucksauswertung wird von dem verwalteten Debugging-Modul geladen. Das verwaltete Debugging-Modul geht davon aus, dass der gesamte Code auf dem lokalen Computer des Benutzers ausgeführt wird. Daher lädt die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT-Datei auf den lokalen Computer des Benutzers. Die Möglichkeit einer Anhebung der Ausführungsberechtigung wird dadurch minimiert, dass alle XSLT-Transformationen in einer neuen Anwendungsdomäne mit eingeschränkten Berechtigungen ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Anwendungsdomänen](/dotnet/framework/app-domains/application-domains)
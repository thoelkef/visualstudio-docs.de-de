---
title: Sicherheitsüberlegungen beim Arbeiten mit XML-Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656140"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Sicherheitsaspekte beim Arbeiten mit XML-Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden Sicherheitsaspekte erörtert, mit denen Sie beim Arbeiten mit dem XML-Editor oder dem XSLT-Debugger vertraut sein müssen.

## <a name="xml-editor"></a>XML-Editor
 Der XML-Editor basiert auf dem Texteditor von Visual Studio. Er beruht auf der <xref:System.Xml>-Klasse und der <xref:System.Xml.Xsl>-Klasse zum Behandeln vieler XML-Prozesse.

- XSLT-Transformationen werden in einer neuen Anwendungsdomäne ausgeführt. Die XSLT-Transformationen sind *sandboxed*. Das heißt, dass mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets bestimmt werden. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse wird XSLT in die Microsoft Intermediate Language (MSIL) kompiliert, um eine höhere Leistung bei der Ausführung zu erzielen.

- Schemata, die auf einen externen Speicherort in der Katalogdatei zeigen, werden beim ersten Laden des XML-Editors automatisch heruntergeladen. Mithilfe der <xref:System.Xml.Schema.XmlSchemaSet>-Klasse werden Schemata kompiliert. Die mit dem XML-Editor gelieferte Katalogdatei weist keine Links zu externen Schemata auf. Bevor der XML-Editor die Schemadatei herunterlädt, muss der Benutzer explizit einen Verweis auf das externe Schema hinzufügen. Das Herunterladen von http kann über die **Options Seite verschiedene Tools** für den XML-Editor deaktiviert werden.

- Der XML-Editor verwendet die <xref:System.Net>-Klassen für Downloads von Schemata.

## <a name="xslt-debugger"></a>XSLT-Debugger
 Der XSLT-Debugger verwendet aus Visual Studio die verwaltete Debug-Engine und die verwalteten Klassen aus dem <xref:System.Xml>-Namespace und dem <xref:System.Xml.Xsl>-Namespace.

- Der XSLT-Debugger führt jede XSLT-Transformation in einer Sandbox-Anwendungsdomäne aus. Mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers werden die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets ermittelt. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.

- Das XSLT-Stylesheet wird mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse kompiliert.

- Die XSLT-Ausdrucksauswertung wird von der verwalteten Debug-Engine geladen. Die verwaltete Debug-Engine geht davon aus, dass der gesamte Code auf dem lokalen Computer des Benutzers ausgeführt wird. Daher lädt die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT-Datei auf den lokalen Computer des Benutzers. Die Möglichkeit einer Anhebung der Ausführungsberechtigung wird dadurch minimiert, dass alle XSLT-Transformationen in einer neuen Anwendungsdomäne mit eingeschränkten Berechtigungen ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
 [Anwendungsdomänen](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)

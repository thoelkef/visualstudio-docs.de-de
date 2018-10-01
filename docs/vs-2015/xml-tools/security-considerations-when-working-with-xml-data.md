---
title: Überlegungen zur Sicherheit bei der Arbeit mit XML-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9acd701c4e279d02cae874768b18a3d89b58203d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513521"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Sicherheitsaspekte beim Arbeiten mit XML-Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Sicherheitsaspekte beim Arbeiten mit XML-Daten](https://docs.microsoft.com/visualstudio/xml-tools/security-considerations-when-working-with-xml-data).  
  
  
In diesem Thema werden Sicherheitsaspekte erörtert, mit denen Sie beim Arbeiten mit dem XML-Editor oder dem XSLT-Debugger vertraut sein müssen.  
  
## <a name="xml-editor"></a>XML-Editor  
 Der XML-Editor basiert auf dem Texteditor von Visual Studio. Er beruht auf der <xref:System.Xml>-Klasse und der <xref:System.Xml.Xsl>-Klasse zum Behandeln vieler XML-Prozesse.  
  
-   XSLT-Transformationen werden in einer neuen Anwendungsdomäne ausgeführt. Die XSLT-Transformationen sind *Sandbox*; also wird die Sicherheitsrichtlinie für Codezugriff Ihres Computers verwendet, um zu bestimmen, die eingeschränkten Berechtigungen, die basierend auf, in dem das XSLT-Stylesheet befindet. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.  
  
-   Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse wird XSLT in die Microsoft Intermediate Language (MSIL) kompiliert, um eine höhere Leistung bei der Ausführung zu erzielen.  
  
-   Schemata, die auf einen externen Speicherort in der Katalogdatei zeigen, werden beim ersten Laden des XML-Editors automatisch heruntergeladen. Mithilfe der <xref:System.Xml.Schema.XmlSchemaSet>-Klasse werden Schemata kompiliert. Die mit dem XML-Editor gelieferte Katalogdatei weist keine Links zu externen Schemata auf. Bevor der XML-Editor die Schemadatei herunterlädt, muss der Benutzer explizit einen Verweis auf das externe Schema hinzufügen. HTTP-Downloads kann deaktiviert werden, über die **verschiedene Extras/Optionen** Seite für die XML-Editor.  
  
-   Der XML-Editor verwendet die <xref:System.Net>-Klassen für Downloads von Schemata.  
  
## <a name="xslt-debugger"></a>XSLT-Debugger  
 Der XSLT-Debugger verwendet aus Visual Studio das verwaltete Debugging-Modul und die verwalteten Klassen aus dem <xref:System.Xml>-Namespace und dem <xref:System.Xml.Xsl>-Namespace.  
  
-   Der XSLT-Debugger führt jede XSLT-Transformation in einer Sandbox-Anwendungsdomäne aus. Mithilfe der Sicherheitsrichtlinie für den Codezugriff Ihres Computers werden die eingeschränkten Berechtigungen anhand des Speicherorts des XSLT-Stylesheets ermittelt. Stylesheets von einem Internetspeicherort weisen die am stärksten eingeschränkten Berechtigungen auf, während auf die Festplatte kopierte Stylesheets mit voller Vertrauenswürdigkeit ausgeführt werden.  
  
-   Das XSLT-Stylesheet wird mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse kompiliert.  
  
-   Die XSLT-Ausdrucksauswertung wird von dem verwalteten Debugging-Modul geladen. Das verwaltete Debugging-Modul geht davon aus, dass der gesamte Code auf dem lokalen Computer des Benutzers ausgeführt wird. Daher lädt die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT-Datei auf den lokalen Computer des Benutzers. Die Möglichkeit einer Anhebung der Ausführungsberechtigung wird dadurch minimiert, dass alle XSLT-Transformationen in einer neuen Anwendungsdomäne mit eingeschränkten Berechtigungen ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsdomänen](http://msdn.microsoft.com/en-us/39e57d07-a740-4cd4-ae82-e119ea3856c1)




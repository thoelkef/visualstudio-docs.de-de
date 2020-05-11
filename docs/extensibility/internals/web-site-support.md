---
title: Website-Support | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703444"
---
# <a name="web-site-support"></a>Websiteunterstützung
Ein Websiteprojektsystem ist ein Projektsystem, das Webprojekte erstellt. Webprojekte wiederum erstellen Webanwendungen. Ein Websiteprojekt generiert eine ausführbare Datei für jede Webseite mit zugeordnetem Code. Zusätzliche ausführbare Dateien werden aus den Quellcodedateien im Ordner /App_Code generiert.

 Websiteprojektsysteme werden erstellt, indem einem vorhandenen Projektsystem Vorlagen und Registrierungsattribute hinzugefügt werden. Eines dieser Attribute wählt den IntelliSense-Anbieter für die Sprache aus. Die IntelliSense-Anbieterimplementierung verarbeitet Verweise und ruft den Sprachcompiler auf, wenn eine intelligente Webseite angefordert wird, die nicht zwischengespeichert wird.

 Der Sprachcompiler, der zum Kompilieren von Webseiten verwendet wird, muss bei [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]registriert sein. Sie können [ \<](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) den Compiler> Element in einer Web.config-Datei verwenden, um den Compiler zu registrieren, wie im folgenden Beispiel:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>In diesem Abschnitt
- [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md)

 Listet die Vorlagen auf, die Sie zum Erstellen neuer Websiteprojekte und zugehöriger Elemente verwenden können.

- [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md)

 Stellt die Registrierungsattribute vor, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]Websiteprojekt mit und verbinden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Webprojekte](../../extensibility/internals/web-projects.md)

 Enthält einen Überblick über die beiden Arten von Webprojekten, Websiteprojekte und Webanwendungsprojekte.

---
title: Registrieren von Einzelnen Dateigeneratoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705811"
---
# <a name="registering-single-file-generators"></a>Registrieren von Generatoren einzelner Dateien
Um ein benutzerdefiniertes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tool in verfügbar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zu machen, müssen Sie es registrieren, damit es instanziiert und einem bestimmten Projekttyp zugeordnet werden kann.

### <a name="to-register-a-custom-tool"></a>So registrieren Sie ein benutzerdefiniertes Tool

1. Registrieren Sie die benutzerdefinierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tool-DLL entweder in der lokalen Registrierung oder in der Systemregistrierung unter HKEY_CLASSES_ROOT.

    Hier sind z. B. die Registrierungsinformationen für das benutzerdefinierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tool MSDataSetGenerator, das mit folgt:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Erstellen Sie einen Registrierungsschlüssel in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der\\gewünschten Struktur unter Generators*GUID,* wobei *GUID* die GUID ist, die durch das Projektsystem oder den Dienst der jeweiligen Sprache definiert wird. Der Name des Schlüssels wird zum programmgesteuerten Namen Ihres benutzerdefinierten Tools. Der benutzerdefinierte Werkzeugschlüssel hat die folgenden Werte:

   - (Standardwert)

        Optional. Stellt eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools bereit. Dieser Parameter ist optional, wird jedoch empfohlen.

   - CLSID

        Erforderlich. Gibt den Bezeichner der Klassenbibliothek der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>COM-Komponente an, die implementiert.

   - GeneratesDesignTimeSource

        Erforderlich. Gibt an, ob Typen aus Dateien, die von diesem benutzerdefinierten Tool erstellt wurden, visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss (Null) 0 für Typen sein, die für visuelle Designer nicht verfügbar sind, oder (eins) 1 für Typen, die visuellen Designern zur Verfügung stehen.

   > [!NOTE]
   > Sie müssen das benutzerdefinierte Tool für jede Sprache, für die das benutzerdefinierte Tool verfügbar sein soll, separat registrieren.

    Der MSDataSetGenerator registriert sich z. B. einmal für jede Sprache:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)
- [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Einführung in das BuildManager-Objekt](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

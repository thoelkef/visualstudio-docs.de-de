---
title: Registrieren von Generatoren einzelner Dateien | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f16385452fa0fa0f4e706da1856185355aa95a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047188"
---
# <a name="registering-single-file-generators"></a>Registrieren von Generatoren einzelner Dateien
Ein benutzerdefiniertes Tool in zur Verfügung stellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie ihn also registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können instanziieren und verknüpft es mit einem bestimmten Projekttyp.

### <a name="to-register-a-custom-tool"></a>Registrieren Sie ein benutzerdefiniertes tool

1. Registrieren Sie das benutzerdefinierte Tool DLL entweder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokale Registrierung oder in der Registrierung des Systems unter HKEY_CLASSES_ROOT.

    Hier ist z. B. die Registrierungsinformationen für das verwaltete MSDataSetGenerator benutzerdefiniertes Tool, das mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Erstellen Sie einen Registrierungsschlüssel in der gewünschten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hive unter Generatoren\\*GUID* , in denen *GUID* wird die GUID, die durch der spezifischen Sprache Projektsystem oder Dienst definiert. Der Name des Schlüssels wird der programmgesteuerte Name des benutzerdefinierten Tools. Der benutzerdefinierte Schlüssel hat die folgenden Werte:

   - (Standard)

        Dies ist optional. Stellt eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools bereit. Dieser Parameter ist optional, jedoch empfohlen.

   - CLSID

        Erforderlich. Gibt den Bezeichner der Klassenbibliothek von COM-Komponente, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.

   - GeneratesDesignTimeSource

        Erforderlich. Gibt an, ob die Typen von Dateien, die von diesem benutzerdefinierten Tool erzeugt visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss 0 (null) Typen für visuelle Designer nicht verfügbar sind oder (1) 1 für Typen, die für den visuellen Designern verfügbar sein.

   > [!NOTE]
   >  Sie müssen das benutzerdefinierte Tool für jede Sprache einzeln registrieren, für die das benutzerdefinierte Tool verfügbar sein soll.

    Zum Beispiel registriert die MSDataSetGenerator sich einmal für jede Sprache:

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

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)
- [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Einführung in das BuildManager-Objekt](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
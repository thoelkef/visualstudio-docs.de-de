---
title: Einzeldatei-Generatoren zu registrieren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9b7d16a9e473028d85540f4447d9981382be0fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132174"
---
# <a name="registering-single-file-generators"></a>Registrieren von Einzeldatei-Generatoren
Um ein benutzerdefiniertes Tool in verfügbar zu machen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie ihn so registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können instanziiert und ordnet sie einen bestimmten Projekttyp.  
  
### <a name="to-register-a-custom-tool"></a>So registrieren ein benutzerdefiniertes tool  
  
1.  Registrieren Sie das benutzerdefinierte Tool DLL entweder in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokale Registrierung oder in der systemregistrierung unter HKEY_CLASSES_ROOT.  
  
     Hier ist z. B. die Registrierungsinformationen für das verwaltete MSDataSetGenerator benutzerdefinierte Tool, das im Lieferumfang [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Erstellen Sie einen Registrierungsschlüssel in der gewünschten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hive unter Generatoren\\*GUID* , in denen *GUID* ist die GUID, die vom Projektsystem der spezifischen Sprache oder vom Dienst definiert. Der Name des Schlüssels wird der programmgesteuerte Name des benutzerdefinierten Tools. Der Schlüssel des benutzerdefinierten Tools hat die folgenden Werte:  
  
    -   (Standard)  
  
         Dies ist optional. Bietet eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools. Dieser Parameter ist optional, jedoch empfohlen.  
  
    -   CLSID  
  
         Erforderlich. Gibt den Bezeichner der COM-Komponente, die implementiert der Klassenbibliothek <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Erforderlich. Gibt an, ob die Typen von Dateien, die von diesem benutzerdefinierten Tool visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss (0) NULL für Typen, die für visuelle Designer nicht verfügbar sind oder für Typen, die visuellen Designern zur Verfügung (1) 1 sein.  
  
    > [!NOTE]
    >  Sie müssen das benutzerdefinierte Tool separat für jede Sprache registrieren, für die benutzerdefinierten Tools verfügbar sein soll.  
  
     Zum Beispiel registriert der MSDataSetGenerator selbst einmal für jede Sprache:  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementieren von Einzeldatei Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Verfügbarmachen von Typen in visuellen Designern](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Einführung in das BuildManager-Objekt](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
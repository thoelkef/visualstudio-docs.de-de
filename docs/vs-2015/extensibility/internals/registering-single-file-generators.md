---
title: Registrieren von einzelnen Datei Generatoren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696100"
---
# <a name="registering-single-file-generators"></a>Registrieren von Generatoren einzelner Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um ein benutzerdefiniertes Tool in verfügbar zu machen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , müssen Sie es registrieren, damit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es instanziieren und einem bestimmten Projekttyp zuordnen kann.  
  
### <a name="to-register-a-custom-tool"></a>So registrieren Sie ein benutzerdefiniertes Tool  
  
1. Registrieren Sie die benutzerdefinierte Tool-DLL entweder in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lokalen Registrierung oder in der Systemregistrierung unter HKEY_CLASSES_ROOT.  
  
     Hier sind z. b. die Registrierungsinformationen für das verwaltete MSDataSetGenerator-Tool, das Folgendes enthält [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Erstellen Sie einen Registrierungsschlüssel im gewünschten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hive unter der Generatoren \\ -*GUID* , wobei *GUID* die GUID ist, die durch das Projekt System oder den Dienst der jeweiligen Sprache definiert ist. Der Name des Schlüssels wird zum programmgesteuerten Namen Ihres benutzerdefinierten Tools. Der benutzerdefinierte Tool Schlüssel weist die folgenden Werte auf:  
  
    - (Standardwert)  
  
         Optional. Stellt eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools bereit. Dieser Parameter ist optional, wird jedoch empfohlen.  
  
    - CLSID  
  
         Erforderlich. Gibt den Bezeichner der Klassenbibliothek der COM-Komponente an, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - Generatesdesigntimesource  
  
         Erforderlich. Gibt an, ob Typen aus Dateien, die von diesem benutzerdefinierten Tool erstellt werden, visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss (0) 0 (null) für Typen sein, die für visuelle Designer nicht verfügbar sind, oder (1) 1 für Typen, die visuellen Designern zur Verfügung stehen.  
  
    > [!NOTE]
    > Sie müssen das benutzerdefinierte Tool separat für jede Sprache registrieren, für die das benutzerdefinierte Tool verfügbar sein soll.  
  
     Der MSDataSetGenerator registriert sich z. b. einmal für jede Sprache:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementieren von Einzel Datei-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Bestimmen des Standard Namespace eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Verfügbar machen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Einführung in das BuildManager-Objekt](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

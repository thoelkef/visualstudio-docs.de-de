---
title: "Registrieren von .NET Framework-Erweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verweise hinzufügen (Dialogfeld), Registrieren von .NET Framework-Erweiterungen"
  - "MSBuild, Registrieren von .NET Framework-Erweiterungen"
  - ".NET Framework-Erweiterungen, Registrieren"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Registrieren von .NET Framework-Erweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Assembly entwickeln, die eine bestimmte Version von .NET Framework erweitert.  Damit die Assembly im Visual Studio\-Dialogfeld **Verweise hinzufügen** erscheint, müssen Sie den Ordner, der die Assembly enthält, der Systemregistrierung hinzufügen.  
  
 Angenommen, das Trey Research\-Unternehmen hat eine Bibliothek entwickelt, die .NET Framework 4 erweitert. Die Bibliothekassemblys sollen im Dialogfeld **Verweise hinzufügen** erscheinen, wenn ein Projekt für .NET Framework 4 bestimmt ist.  Zudem wird angenommen, dass es sich um 32\-Bit\-Assemblys zur Ausführung auf einem 32\-Bit\-Computer oder um 64\-Bit\-Assemblys zur Ausführung auf einem 64\-Bit\-Computer handelt, die im Ordner "C:\\TreyResearch\\Extensions4\\" installiert werden.  
  
 Registrieren Sie diesen Ordner mit dem folgenden Schlüssel: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  Weisen Sie dem Schlüssel diesen Standardwert zu: C:\\TreyResearch\\Extensions4.  
  
> [!NOTE]
>  Die Buildnummer der .NET Framework\-Version ist möglicherweise anders.  
  
 Um eine 32\-Bit\-Assembly auf einem 64\-Bit\-Computer zu registrieren, verwenden Sie den Wow6432\-Knoten. Beispiel: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  
  
## Siehe auch  
 [Integration von Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
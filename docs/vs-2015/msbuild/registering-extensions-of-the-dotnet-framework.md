---
title: Registrieren von .NET Framework-Erweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5963faa5acb72ab0c94ca6b346456d83276e361
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445230"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrieren von .NET Framework-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Assembly entwickeln, die eine bestimmte Version von .NET Framework erweitert. Damit die Assembly im Dialogfeld **Verweise hinzufügen** in Visual Studio angezeigt wird, müssen Sie den Ordner, in dem sie enthalten ist, zur Systemregistrierung hinzufügen.  
  
 Nehmen wir beispielsweise an, dass das Unternehmen Trey Research eine Bibliothek entwickelt hat, die .NET Framework 4 erweitert, und möchte, dass die Bibliothekassemblys im Dialogfeld **Verweise hinzufügen** angezeigt werden, wenn ein Projekt auf .NET Framework 4 abzielt. Darüber hinaus wird angenommen, dass die Assemblys 32-Bit-Assemblys zur Ausführung auf einem 32-Bit-Computer oder 64-Bit-Assemblys zur Ausführung auf einem 64-Bit-Computer sind und dass sie im Ordner C:\TreyResearch\Extensions4\ installiert werden.  
  
 Registrieren Sie diesen Ordner mithilfe des folgenden Schlüssels: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Weisen Sie dem Schlüssel diesen Standardwert zu: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
> Die Buildnummer der Version von .NET Framework kann abweichen.  
  
 Verwenden Sie den Wow6432-Knoten, um wie im folgenden Beispiel eine 32-Bit-Assembly auf einem 64-Bit-Computer zu registrieren: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Integration](../msbuild/visual-studio-integration-msbuild.md)

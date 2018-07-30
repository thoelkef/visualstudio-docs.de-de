---
title: Registrieren von .NET Framework-Erweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0017255b67042a7e42b54325b24512a295ebeaf5
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180151"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrieren von .NET Framework-Erweiterungen
Sie können eine Assembly entwickeln, die eine bestimmte Version von .NET Framework erweitert. Damit die Assembly im Dialogfeld **Verweise hinzufügen** in Visual Studio angezeigt wird, müssen Sie den Ordner, in dem sie enthalten ist, zur Systemregistrierung hinzufügen.  
  
 Nehmen wir beispielsweise an, dass das Unternehmen Trey Research eine Bibliothek entwickelt hat, die .NET Framework 4 erweitert, und möchte, dass die Bibliothekassemblys im Dialogfeld **Verweise hinzufügen** angezeigt werden, wenn ein Projekt auf .NET Framework 4 abzielt. Darüber hinaus wird angenommen, dass die Assemblys 32-Bit-Assemblys zur Ausführung auf einem 32-Bit-Computer oder 64-Bit-Assemblys zur Ausführung auf einem 64-Bit-Computer sind und im Ordner *C:\TreyResearch\Extensions4\\* installiert werden.  
  
 Registrieren Sie diesen Ordner mithilfe dieses Schlüssels: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Weisen Sie dem Schlüssel diesen Standardwert zu: **C:\TreyResearch\Extensions4**.  
  
> [!NOTE]
>  Die Buildnummer der Version von .NET Framework kann abweichen.  
  
 Um eine 32-Bit-Assembly auf einem 64-Bit-Computer zu registrieren, verwenden Sie den Wow6432-Knoten, z.B.: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.  
  
### <a name="see-also"></a>Siehe auch  
 [Integration von Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
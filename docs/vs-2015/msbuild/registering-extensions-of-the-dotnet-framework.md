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
ms.openlocfilehash: 18df04fc706ea716f7c22baa6508930f0f94a6f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801465"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrieren von .NET Framework-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können eine Assembly entwickeln, die eine bestimmte Version von .NET Framework erweitert. Damit die Assembly im Dialogfeld **Verweise hinzufügen** in Visual Studio angezeigt wird, müssen Sie den Ordner, in dem sie enthalten ist, zur Systemregistrierung hinzufügen.  
  
 Nehmen wir beispielsweise an, dass das Unternehmen Trey Research eine Bibliothek entwickelt hat, die .NET Framework 4 erweitert, und möchte, dass die Bibliothekassemblys im Dialogfeld **Verweise hinzufügen** angezeigt werden, wenn ein Projekt auf .NET Framework 4 abzielt. Darüber hinaus wird angenommen, dass die Assemblys 32-Bit-Assemblys zur Ausführung auf einem 32-Bit-Computer oder 64-Bit-Assemblys zur Ausführung auf einem 64-Bit-Computer sind und dass sie im Ordner C:\TreyResearch\Extensions4\ installiert werden.  
  
 Registrieren Sie diesen Ordner mithilfe dieses Schlüssels: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Weisen Sie dem Schlüssel diesen Standardwert: C:\TreyResearch\Extensions4 zu.  
  
> [!NOTE]
>  Die Buildnummer der Version von .NET Framework kann abweichen.  
  
 Um eine 32-Bit-Assembly auf einem 64-Bit-Computer zu registrieren, verwenden Sie den Wow6432-Knoten, z.B.: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Integration](../msbuild/visual-studio-integration-msbuild.md)

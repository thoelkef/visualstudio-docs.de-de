---
title: Auflösen von Assemblys zur Entwurfszeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 920e7222b3b425cbb13c962ff8c2e1e2fc551bd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159228"
---
# <a name="resolving-assemblies-at-design-time"></a>Auflösen von Assemblys zur Entwurfszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie über die Registerkarte ".NET" des Dialogfelds "Verweis hinzufügen" einen Verweis auf eine Assembly hinzufügen, zeigt der Verweis auf eine Zwischenverweisassembly, also eine Assembly, die alle Typ- und Signaturinformationen, aber nicht notwendigerweise Code enthält. Auf der Registerkarte ".NET" sind Verweisassemblys aufgeführt, die Laufzeitassemblys in .NET Framework entsprechen. Außerdem werden Verweisassemblys aufgeführt, die den Laufzeitassemblys in den von Drittanbietern verwendeten registrierten AssemblyFoldersEx-Ordnern entsprechen.  
  
## <a name="multi-targeting"></a>Festlegung von Zielversionen  
 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ermöglicht die Ausrichtung auf Versionen von .NET-Framework, die mit der Common Language Runtime (CLR) Version 2.0 oder Version 4 ausgeführt werden. Dies schließt die .NET Framework-Versionen 2.0, 3.0, 3.5, 4, 4.5 und 4.5.1 sowie die Silverlight-Versionen 1.0, 2.0 und 3.0 ein. Wenn eine neue auf CLR, Version 2.0 oder Version 4, basierte .NET Framework-Version veröffentlicht wird, kann das Framework mit einem Paket zur Festlegung von Zielversionen installiert werden und wird automatisch als Ziel in Visual Studio angezeigt.  
  
## <a name="how-type-resolution-works"></a>So funktioniert Typauflösung  
 Zur Laufzeit löst die CLR die Typen in der Assembly auf, indem sie die GAC, das Verzeichnis "bin" und alle Prüfpfade durchsucht. Dies wird vom Fusion-Ladeprogramm gehandhabt. Aber woher weiß das Fusion-Ladeprogramm, wonach gesucht werden soll? Dies hängt von der zur Entwurfszeit (als die Anwendung erstellt wurde) festgelegten Auflösung ab.  
  
 Während des Builds löst der Compiler mithilfe von Verweisassemblys Anwendungstypen auf. In den Versionen 2.0, 3.0 3.5, 4, 4.5 und 4.5.1 von .NET Framework werden die Verweisassemblys bei der Installation von .NET Framework mitinstalliert.  
  
 Die Verweisassemblys werden durch das Paket zur Festlegung von Zielversionen bereitgestellt, das mit der entsprechenden Version des .NET Framework-SDKs geliefert wird. Das Framework selbst stellt nur die Laufzeitassemblys bereit. Zur Erstellung von Anwendungen müssen sowohl .NET Framework als auch das entsprechende .NET Framework-SDK installiert werden.  
  
 Wenn Sie auf eine bestimmte Version von .NET Framework abzielen, löst das Buildsystem mithilfe der Verweisassemblys im Paket zur Festlegung von Zielversionen alle Typen auf. Zur Laufzeit löst das Fusion-Ladeprogramm dieselben Typen in die Laufzeitassemblys auf, die sich in der Regel im GAC befinden.  
  
 Wenn Verweisassemblys nicht verfügbar sind, löst das Buildsystem Assemblytypen mithilfe der Laufzeitassemblys auf. Da Laufzeitassemblys im GAC nicht durch Nebenversionsnummern unterschieden werden, ist es möglich, dass die falsche Assembly aufgelöst wird. Dies könnte beispielsweise geschehen, wenn beim Abzielen auf Version 3.0 auf eine neue in .NET Framework, Version 3.5, eingeführte Methode verwiesen wird. Der Build wird erfolgreich erstellt, und die Anwendung wird auf dem Buildcomputer ausgeführt, ist aber nur auf Computern lauffähig, auf denen Version 3.5 installiert ist.  
  
 Das Paket zur Festlegung von Zielversionen, das jetzt mit dem .NET Framework-SDK geliefert wird, enthält eine Liste (auch Neuverteilungsliste (redist) genannt) aller Laufzeitassemblys dieser Version des Frameworks. So können die Typen vom Buildsystem nicht mehr in die falsche Version der Assembly aufgelöst werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konzepte](../msbuild/msbuild-advanced-concepts.md)

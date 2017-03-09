---
title: "Problembehandlung bei Ausnahmen: System.BadImageFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "BadImageFormatException-Klasse"
ms.assetid: 8d2b385a-3d6d-4dfa-8546-7ece562867e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.BadImageFormatException
Eine <xref:System.BadImageFormatException>\-Ausnahme wird ausgelöst, wenn das Dateibild einer DLL oder eines ausführbaren Programms ungültig ist.  
  
## Tipps  
 **Wenn von Ihrer Anwendung 32\-Bit\-Komponenten verwendet werden, muss sie immer als 32\-Bit\-Anwendung ausgeführt werden.**  
 Wenn die Eigenschaft **Zielplattform** für das Anwendungsprojekt auf `AnyCPU` festgelegt ist, kann die kompilierte Anwendung entweder im 64\-Bit\- oder 32\-Bit\-Modus ausgeführt werden. Wenn sie als 64\-Bit\-Anwendung ausgeführt wird, generiert der JIT\-Compiler \(Just\-In\-Time\) 64\-Bit\-maschinenabhängige Sprache. Wenn die Anwendung von einer verwalteten oder nicht verwalteten 32\-Bit\-Komponente abhängt, kann diese Komponente nicht im 64\-Bit\-Modus geladen werden. Um dieses Problem zu beheben, legen Sie die Eigenschaft **Zielplattform** auf `x86` fest, und führen Sie erneut eine Kompilierung aus.  
  
 **Sie dürfen keine Komponente verwenden, die mit einer anderen Version von .NET Framework erstellt wurde.**  
 Diese Ausnahme wird ausgelöst, wenn eine Anwendung oder Komponente, die mit [!INCLUDE[net_v10_short](../misc/includes/net_v10_short_md.md)] oder [!INCLUDE[net_v11_short](../misc/includes/net_v11_short_md.md)] entwickelt wurde, versucht, eine Assembly zu laden, die mit [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] oder höher entwickelt wurde, oder wenn eine Anwendung, die mit [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] oder [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] entwickelt wurde, versucht, eine Assembly zu laden, die mit [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] entwickelt wurde. Die <xref:System.BadImageFormatException>\-Ausnahme wird möglicherweise als Kompilierzeitfehler gemeldet, oder die Ausnahme wird unter Umständen während der Laufzeit ausgelöst. In der <xref:System.BadImageFormatException>\-Klasse finden Sie ein Beispiel.  
  
 **Stellen Sie sicher, dass das Dateibild eine gültige verwaltete Assembly oder ein gültiges verwaltetes Modul ist.**  
 Diese Ausnahme wird ausgelöst, wenn eine nicht verwaltete DLL \(Dynamic Link Library\) oder eine ausführbare Datei an die <xref:System.Reflection.Assembly.Load%2A>\-Methode zum Laden übergeben wird.  
  
 Visual Basic\-Benutzer finden weitere Informationen unter [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
## Hinweise  
 Diese Ausnahme kann durch Reflektion auf ausführbare Dateien in C\+\+ ausgelöst werden. Meistens hat dabei der C\+\+\-Compiler die Umsetzungsadressen oder den .Reloc\-Abschnitt der ausführbaren Datei entfernt. Damit die Umsetzungsadresse in einer ausführbaren Datei in C\+\+ erhalten bleibt, geben Sie beim Verknüpfen **\/fixed:no** an.  
  
 Weitere Ursachen dieser Ausnahme finden Sie in der <xref:System.BadImageFormatException>\-Klasse.  
  
## Siehe auch  
 <xref:System.BadImageFormatException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
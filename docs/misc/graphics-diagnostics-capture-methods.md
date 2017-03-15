---
title: "Erfassungsmethoden der Grafikdiagnose | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# Erfassungsmethoden der Grafikdiagnose
Fügen Sie hier eine Einleitung ein.  
  
## Erfassungsmethoden  
 In [!INCLUDE[win81](../debugger/includes/win81_md.md)] kann die DirectX 11.2 Runtime Grafikinformationen mithilfe von Debugging\-Tools wie der Grafikdagnose intern erfassen – dies ist als *stabile Erfassung* bekannt.  Bevor dieser Support zu Direct Runtime hinzugefügt wurde, wurden Grafikinformationen durch Abfangen bestimmter DirectX\-Funktionsaufrufe zur Aufzeichnung von Argumenten und anderen Informationen vor der Weiterleitung der Aufrufe zum Abschluss an DirectX erfasst – dies wird *Legacy\-Erfassung* genannt.  
  
 Da DirectX Runtime exklusiv für die Erfassung von Grafikinformationen in [!INCLUDE[win81](../debugger/includes/win81_md.md)] verantwortlich ist, muss die Legacy\-Erfassung nicht aktualisiert werden, um DirectX 11.2 zu unterstützen. Deshalb ist die Legacy\-Erfassung veraltet.  Da allerdings DirectX 11.2 Runtime keine Versionen von Windows vor [!INCLUDE[win81](../debugger/includes/win81_md.md)] unterstützt, wird in [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] weiterhin die Legacy\-Erfassung für Apps unterstützt, die für [!INCLUDE[win8](../debugger/includes/win8_md.md)] und [!INCLUDE[win7](../debugger/includes/win7_md.md)] ausgelegt sind.  
  
 Mit beiden Methoden werden ähnliche Informationen aufgezeichnet, und es wird nicht geändert, wie Grafikinformationen erfasst werden oder die Grafikdiagnose\-Tools verwendet werden.  
  
### Stabile Erfassung  
 Die stabile Erfassung unterstützt [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]\-Grafikdiagnosen unter [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] und Windows Phone 8.1.  Es unterstützt DirectX 10.0 bis DirectX 11.2 und kann Grafikinformationen über neue Direct3D 11.2\-Funktionen erfassen – z. B. unterteilte Ressourcen.  Allerdings unterstützt es nicht vollständig alle Funktionen von Direct3D 11.2 – Sie können z. B. keinen HLSL\-Shader debuggen, der mithilfe der HLSL Shader\-Verknüpfungsfunktion erstellt wurde.  Die stabile Erfassung verwendet eine neue Erfassungs\-API zur Unterstützung ihrer programmierten Erfassungsszenarios.  
  
### Legacy\-Erfassung  
 Die Legacy\-Erfassung unterstützt [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]\- und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]\-Grafikdiagnosen unter [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows RT 8 und [!INCLUDE[win7](../debugger/includes/win7_md.md)].  Sie unterstützt DirectX 10.0 bis DirectX 11.1.  Die Legacy\-Erfassung unterstützt keine Funktionen von Direct3D 11.2 und ist mit Ausnahme von Szenarien, in denen keine stabile Erfassung zur Verfügung steht, veraltet.  Die Legacy\-Erfassung verwendet die in der Headerdatei `vsgcapture.h` definierte Erfassungs\-API zur Unterstützung ihrer programmierten Erfassungsszenarios.  Diese Art von programmgesteuerter Erfassung ist ebenfalls veraltet \- außer für Szenarien, in denen keine stabile Erfassung zur Verfügung steht.  
  
## Siehe auch  
 [Erfassen von Grafikinformationen](../debugger/capturing-graphics-information.md)   
 [Exemplarische Vorgehensweise: Erfassen von Grafikinformationen](../debugger/walkthrough-capturing-graphics-information.md)
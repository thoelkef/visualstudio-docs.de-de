---
title: "Gewusst wie: Erzwingen eines VSPackage-Ladevorgangs | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, Erzwingen des Ladevorgangs"
  - "VSPackages, laden"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Gewusst wie: Erzwingen eines VSPackage-Ladevorgangs
normalerweise nur VSPackages geladen werden, wenn sich ihre zugehörigen Funktionen erforderlich ist, einen Vorgang abzuschließen.  Unter bestimmten Umständen kann ein VSPackage muss jedoch VSPackages geladen werden soll, ein anderes erzwingen.  Zum Beispiel könnte ein größeres VSPackage Leichtgewichtler Programmierung in einem VSPackage Kontext nicht als CMDUIContext verfügbar ist.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>\-Methode verwenden, um zu erzwingen, dass VSPackages geladen werden soll.  
  
### So erzwingen Sie VSPackages zu ladende  
  
-   Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackages Methode ein, die ein anderes VSPackage erzwingt, um zu laden:  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     Wenn ein VSPackage initialisiert wird, erzwingt dies `PackageToBeLoaded` , um zu laden.  
  
## Robuste Programmierung  
 Laden aktiviert sollte nicht für VSPackage\-Kommunikation verwendet werden.  Verwenden Sie stattdessen [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md).  
  
## Siehe auch  
 [Verwalten von VSPackages](../extensibility/managing-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
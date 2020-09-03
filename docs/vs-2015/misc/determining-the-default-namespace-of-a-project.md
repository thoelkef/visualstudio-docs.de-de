---
title: Bestimmen des Standard Namespace eines Projekts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705771"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Ermitteln des Standardnamespaces eines Projekts
Wenn für die- [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `CustomToolNamespace` Eigenschaft für die Eingabedatei festgelegt ist, wird der Wert von zum `CustomToolNamespace` Wert des Standard Namespace-Parameters, der an die-Methode übergeben wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> . Andernfalls entspricht der `wszDefaultNamespace` an übergebenen Parameter `Generate` immer dem Root-Namespace. Weitere Informationen zu Namespaces finden Sie unter [Namespace Schlüsselwörter](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] verwendet Ordner basierte Namespaces. Das heißt, der Namespace besteht aus dem Stamm Namespace sowie den Namen aller Ordner, die das benutzerdefinierte Tool enthalten. Jeder Ordnername wird in einen gültigen Bezeichner konvertiert, und Zeiträume trennen alle Namen. Wenn z. b. die Eingabedatei FolderA\FolderB\FolderC\MyInput.txt ist und der Stamm Namespace CL9 ist, ist der berechnete Standard Namespace **CL9. FolderA. folderB. folderc**.  
  
 Eine Ausnahme zu dieser Regel tritt auf, wenn die Hierarchie Kette einen Webverweis Ordner enthält. Beispiel:  
  
- Folderc war ein Webverweis Ordner, der Namespace **CL9. Folderc**.  
  
- FolderB war ein Webverweis Ordner, der Namespace **CL9. FolderB. folderc**.  
  
  Das heißt, der Namespace verwendet das folgende Format:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Einzel Datei-Generatoren](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrieren von einzelnen Datei Generatoren](../extensibility/internals/registering-single-file-generators.md)   
 [Verfügbarmachen von Typen für visuelle Designer](../extensibility/internals/exposing-types-to-visual-designers.md)
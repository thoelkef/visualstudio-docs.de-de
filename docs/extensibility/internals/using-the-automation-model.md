---
title: Mithilfe des Automatisierungsmodells | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 5655168e868e34befe83521a17b124c58be816b7
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-automation-model"></a>Mithilfe des Automatisierungsmodells
Nachdem Sie Ihr VSPackage Automation verbunden haben, Sie erhalten die Eigenschaften und Methoden durch Aufrufen der <xref:EnvDTE.DTEClass.GetObject%2A>-Methode für die <xref:EnvDTE._DTE>Objekt auf und übergibt eine Zeichenfolge, die das Objekt, das Sie abrufen möchten.</xref:EnvDTE._DTE> </xref:EnvDTE.DTEClass.GetObject%2A>  
  
## <a name="obtaining-project-objects"></a>Abrufen von Project-Objekte  
 Es folgen zwei Codebeispiele, die zeigen, wie ein Consumer Automatisierung des Projekts Automatisierungsobjekte erhält. Informationen zum Abrufen des DTE-Objekts finden Sie unter [Gewusst wie: Abrufen Verweise auf DTE und DTE2-Objekt](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb#  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 An diesem Punkt können Sie die standard-Projekt-Objekte, die Teil eines bestimmten VSPackage, das Hierarchiemodell nach oben zu verschieben.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Objekt, das eine Eigenschaft eines benutzerdefinierten Typs ist.:  
  
```vb#  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Der folgende Code Listet die Namen aller Eigenschaften in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung **allgemeine** auf die option der **Tools** Menü:  
  
```vb#  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.DTEClass.GetObject%2A></xref:EnvDTE.DTEClass.GetObject%2A>

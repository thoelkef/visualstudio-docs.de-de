---
title: Verwenden des Automatisierungs Modells | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675211"
---
# <a name="using-the-automation-model"></a>Verwenden des Automatisierungsmodells
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem Sie das VSPackage mit Automation verbunden haben, können Sie die Eigenschaften und Methoden abrufen, indem Sie die- <xref:EnvDTE.DTEClass.GetObject%2A> Methode für das-Objekt aufrufen und <xref:EnvDTE._DTE> eine Zeichenfolge übergeben, die das Objekt darstellt, das Sie abrufen möchten.  
  
## <a name="obtaining-project-objects"></a>Abrufen von Projekt Objekten  
 Im folgenden finden Sie zwei Codebeispiele, die zeigen, wie ein automatisierungsconsumer die Project Automation-Objekte abruft. Weitere Informationen zum erhalten des DTE-Objekts finden Sie unter Gewusst [wie: verweisen auf die DTE-und DTE2-Objekte](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
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
  
 An diesem Punkt können Sie die Standard Projekt Objekte verwenden, die Teil eines bestimmten VSPackages sind, um das Hierarchie Modell zu verschieben.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Objekt, das eine Eigenschaft eines benutzerdefinierten Projekt Typs ist, angezeigt wird:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Im folgenden Code werden die Namen aller Eigenschaften in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Option Umgebung **Allgemein** im Menü Extras aufgeführt: **Tools**  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:EnvDTE.DTEClass.GetObject%2A>

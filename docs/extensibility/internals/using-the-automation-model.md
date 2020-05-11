---
title: Verwenden des Automatisierungsmodells | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704224"
---
# <a name="using-the-automation-model"></a>Verwenden des Automatisierungsmodells
Nachdem Sie Ihr VSPackage mit der Automatisierung verbunden haben, <xref:EnvDTE.DTEClass.GetObject%2A> können Sie <xref:EnvDTE._DTE> die Eigenschaften und Methoden abrufen, indem Sie die Methode für das Objekt aufrufen und eine Zeichenfolge übergeben, die das Objekt darstellt, das Sie abrufen möchten.

## <a name="obtaining-project-objects"></a>Abrufen von Projektobjekten
 Im Folgenden finden Sie zwei Codebeispiele, die zeigen, wie ein Automatisierungsbenutzer die Projektautomatisierungsobjekte erhält. Informationen zum Abrufen des DTE-Objekts finden Sie unter [Gewusst wie: Abrufen von Verweisen auf die DTE- und DTE2-Objekte](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 An dieser Stelle können Sie die Standardprojektobjekte, die Teil eines bestimmten VSPackage sind, verwenden, um das Hierarchiemodell nach unten zu verschieben.

 Das folgende Codebeispiel zeigt, wie Sie ein benutzerdefiniertes Objekt abrufen, das eine Eigenschaft eines benutzerdefinierten Projekttyps ist:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Der folgende Code listet die Namen aller [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Eigenschaften in der Option Umgebung **Allgemein** im Menü **Extras** auf:

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
- <xref:EnvDTE.DTEClass.GetObject%2A>

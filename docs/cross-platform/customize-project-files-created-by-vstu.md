---
title: "Anpassen von mit VSTU erstellten Projektdateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "crdun"
manager: "crdun"
---
# Anpassen von mit VSTU erstellten Projektdateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio\-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity\-Stil.  Registrieren Sie das `VisualStudioIntegration.ProjectFileGeneration`\-Ereignis, um die Projektdatei zu ändern, immer wenn sie neu erstellt wird.  
  
## Veranschaulicht  
 Anpassen der von Visual Studio\-Tools für Unity generierten Visual Studio\-Projektdateien.  
  
## Beispiel  
  
```c#  
using System;  
using System.IO;  
using System.Linq;  
using System.Text;  
using System.Xml.Linq;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class ProjectFileHook  
{  
    // necessary for XLinq to save the xml project file in utf8  
    class Utf8StringWriter : StringWriter  
    {  
        public override Encoding Encoding  
        {  
            get { return Encoding.UTF8; }  
        }  
    }  
  
    static ProjectFileHook()  
    {  
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>  
        {  
            // parse the document and make some changes  
            var document = XDocument.Parse(content);  
            document.Root.Add(new XComment("FIX ME"));  
  
            // save the changes using the Utf8StringWriter  
            var str = new Utf8StringWriter();  
            document.Save(str);  
  
            return str.ToString();  
        };  
    }  
}  
```  
  
## Siehe auch  
 [Beispiel: Protokollrückruf](../cross-platform/share-the-unity-log-callback-with-vstu.md)
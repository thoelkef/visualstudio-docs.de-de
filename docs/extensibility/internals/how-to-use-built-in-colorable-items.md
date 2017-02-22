---
title: "Gewusst wie: Verwenden von integrierten F&#228;rbbare Elemente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "färbbare Elemente"
  - "Language Services, integrierten färbbare Elemente"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Verwenden von integrierten F&#228;rbbare Elemente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bevor Sie die integrierten färbbaren Elemente verwenden, müssen Sie in der integrierten Entwicklungsumgebung \(IDE\) zuerst dieser signalisieren können nicht zum Bereitstellen, benutzerdefinierte färbbare Elemente besitzen, die in diesem Fall <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>\-Objekte wären.  Hierzu fügen Sie einen Registrierungseintrag für den Sprachdienst festlegen.  
  
### Um die integrierte färbbare Elemente verwenden  
  
1.  Klicken Sie unter HKEY\_LOCAL\_MACHINE \\ VisualStudio \\*X.Y*\\ \\. \\*Sprachenname*Sprachendiensten Sprachen, in denen *X.Y* eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist und *Sprachenname* der Name der Sprache ist, erstellen Sie einen Wert für DWORD\-Registrierungseintrags mit der Bezeichnung `RequestStockColors`.  
  
2.  Legen Sie den Wert des Registrierungseintrags `RequestStockColors` auf 1 fest.  
  
     Nachdem Sie den Registrierungseintrag erstellen, kann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>\-Methode der farbigen Darstellung <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> die Member der Enumeration können Sie das Array der Farben attributen für den Editor zu füllen.  
  
    > [!NOTE]
    >  Legen Sie nicht den Registrierungseintrag fest, wenn Sie benutzerdefinierte färbbare Elemente bereitstellen.  Weitere Informationen finden Sie unter [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md).  
  
## Siehe auch  
 [Syntaxfarben in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Farben für Syntax](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Registrieren einer Legacy\-Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service2.md)
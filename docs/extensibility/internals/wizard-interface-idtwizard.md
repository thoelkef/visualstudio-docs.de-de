---
title: "Assistenten-Benutzeroberfl&#228;che (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDTWizard-Schnittstelle"
  - "Assistenten, Schnittstelle"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Assistenten-Benutzeroberfl&#228;che (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung \(IDE\) verwendet die <xref:EnvDTE.IDTWizard>\-Schnittstelle, um Assistenten zu kommunizieren.  Assistenten müssen diese Schnittstelle implementieren, um in der IDE installiert werden.  
  
 Die <xref:EnvDTE.IDTWizard.Execute%2A>\-Methode ist die einzige Möglichkeit, die mit der <xref:EnvDTE.IDTWizard>\-Schnittstelle zugeordnet ist.  Assistenten implementieren diese Methode und die IDE ruft die Methode auf die Schnittstelle an.  Im folgenden Beispiel wird die Signatur der Methode auf.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Der Mechanismus zur Anfangs\- und ist für die **Neues ProjektNeues Element hinzufügen** Assistenten sehr ähnlich.  Um ein beliebiges zu starten, nennen Sie die <xref:EnvDTE.IDTWizard>\-Schnittstelle definiert in Dteinternal.h.  Der einzige Unterschied ist der Satz der Kontext\- und benutzerdefinierte parametern, die auf die Schnittstelle übergeben werden, wenn die Schnittstelle aufgerufen wird.  
  
 Die folgenden Informationen werden die <xref:EnvDTE.IDTWizard>\-Schnittstelle, die Assistenten implementieren müssen, um im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE funktionieren.  Die IDE ruft die <xref:EnvDTE.IDTWizard.Execute%2A>\-Methode im Assistenten auf und übergibt sie Folgendes:  
  
-   Das DTE\-Objekt  
  
     Das DTE\-Objekt ist das Stammobjekt des Automatisierungsmodells dar.  
  
-   Das Handle für das Fenster, wie im Dialogfeld Codesegment, `hwndOwner ([in] long)`gezeigt.  
  
     Der Assistent verwendet dieses `hwndOwner` als übergeordnetes Element für das Dialogfeld Assistenten.  
  
-   Kontextparameter übergeben auf die Schnittstelle als Variante für ein SAFEARRAY Codesegment zeigt, wie im `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Kontextparameter enthalten ein Array von Werten, die für die Art des Assistenten beziehen, der gestartet wird, und den aktuellen Status des Projekts.  Die IDE führt die Kontextparameter zum Assistenten.  Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
-   Benutzerdefinierte Übergeben von Parametern an die Schnittstelle als Variante für ein SAFEARRAY Codesegment zeigt, wie im `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Benutzerdefinierte Parameter enthalten ein Array benutzerdefinierter Parameter.  Eine VSZ\-Datei führt benutzerdefinierte Parameter an die IDE.  Die Werte werden durch die `Param=`\-Anweisungen bestimmt.  Weitere Informationen finden Sie unter [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).  
  
-   Rückgabewerte für die Schnittstelle sind  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## Siehe auch  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)
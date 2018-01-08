---
title: "Assistenten-Benutzeroberfläche (IDTWizard) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57e3ceda07abadbf00e67e740bd276430157eabe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-interface-idtwizard"></a>Assistenten-Benutzeroberfläche (IDTWizard)
Die integrierte Entwicklungsumgebung (IDE) verwendet die <xref:EnvDTE.IDTWizard> Schnittstelle für die Kommunikation mit dem Assistenten. Assistenten müssen diese Schnittstelle implementieren, um in der IDE installiert werden.  
  
 Die <xref:EnvDTE.IDTWizard.Execute%2A> Methode ist die einzige Methode, die zugeordneten die <xref:EnvDTE.IDTWizard> Schnittstelle. Assistenten implementieren Sie diese Methode, und die IDE Ruft die Methode für die Schnittstelle. Im folgende Beispiel wird die Signatur der Methode.  
  
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
  
 Die Startmechanismus ist für beide ähnlich wie die **neues Projekt** und **neues Element hinzufügen**Assistenten. Um entweder zu starten, rufen Sie die <xref:EnvDTE.IDTWizard> in Dteinternal.h definierten-Schnittstelle. Der einzige Unterschied ist der Satz von Kontext und die benutzerdefinierten Parameter, die auf die Schnittstelle übergeben werden, wenn die Schnittstelle aufgerufen wird.  
  
 Die folgenden Informationen beschreiben die <xref:EnvDTE.IDTWizard> -Schnittstelle, die Assistenten implementieren müssen, um Arbeit die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ruft die IDE die <xref:EnvDTE.IDTWizard.Execute%2A> Methode auf und übergeben sie die folgenden Assistenten:  
  
-   Das DTE-Objekt  
  
     Das DTE-Objekt ist der Stamm das Automatisierungsmodell.  
  
-   Das Handle für das Dialogfeld Fenster entsprechend der Codesegment `hwndOwner ([in] long)`.  
  
     Der Assistent verwendet diese `hwndOwner` als das übergeordnete Element für das Dialogfeld des Assistenten.  
  
-   Kontextparameter übergeben auf die Schnittstelle als Variante für SAFEARRAY wie im Codesegment `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Kontextparameter enthalten ein Array von Werten, die spezifisch für die Art der Assistent gestartet wird und der aktuelle Zustand des Projekts. Die IDE übergibt die Kontextparameter, um dem Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
-   Benutzerdefinierte Parameter auf die Schnittstelle als übergeben eine Variante für SAFEARRAY wie im Codesegment `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Benutzerdefinierte Parameter wird ein Array der benutzerdefinierten Parameter enthalten. VSZ-Datei übergibt benutzerdefinierte Parameter in der IDE an. Die Werte gemäß der `Param=` Anweisungen. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).  
  
-   Rückgabewerte für die Schnittstelle sind  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
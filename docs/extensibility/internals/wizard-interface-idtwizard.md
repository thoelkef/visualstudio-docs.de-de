---
title: Assistentenschnittstelle (IDTWizard) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f1bc71239ff7923676c35496e103223a6b6e56e
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219860"
---
# <a name="wizard-interface-idtwizard"></a>Assistentenschnittstelle (IDTWizard)
Die integrierte Entwicklungsumgebung (IDE) verwendet die <xref:EnvDTE.IDTWizard> Schnittstelle für die Kommunikation mit dem Assistenten. Assistenten müssen diese Schnittstelle implementieren, um in der IDE installiert werden.  
  
 Die <xref:EnvDTE.IDTWizard.Execute%2A> Methode ist die einzige Methode, die zugeordneten der <xref:EnvDTE.IDTWizard> Schnittstelle. Diese Methode implementieren, Assistenten und die IDE Ruft die Methode für die Schnittstelle. Das folgende Beispiel zeigt die Signatur der Methode.  
  
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
  
 Der Startmechanismus ist für beide Plattformen ähnlich der **neues Projekt** und **neues Element hinzufügen** Assistenten. Um zu starten, rufen Sie die <xref:EnvDTE.IDTWizard> in Dteinternal.h definierte Schnittstelle. Der einzige Unterschied ist der Satz von Kontext und den benutzerdefinierten Parametern, die auf die Schnittstelle übergeben werden, wenn die Schnittstelle aufgerufen wird.  
  
 Die folgenden Informationen beschreiben die <xref:EnvDTE.IDTWizard> -Schnittstelle, die Assistenten implementieren müssen, um die Arbeiten in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Die IDE-Aufrufe der <xref:EnvDTE.IDTWizard.Execute%2A> Methode auf und übergeben sie die folgenden Assistenten:  
  
-   Das DTE-Objekt  
  
     Das DTE-Objekt ist der Stamm des Automatisierungsmodells.  
  
-   Das Handle für Fenster, um das Dialogfeld wie in der Codesegment gezeigt `hwndOwner ([in] long)`.  
  
     Der Assistent verwendet diese `hwndOwner` als übergeordnetes Element für das Dialogfeld des Assistenten.  
  
-   Kontextparameter übergeben auf die Schnittstelle als Variante für SAFEARRAY wie gezeigt in das Codesegment `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Kontextparameter enthalten ein Array von Werten, die spezifisch für die Art der Assistent gestartet wird und den aktuellen Status des Projekts. Die IDE übergibt die Kontextparameter, um dem Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
-   Benutzerdefinierte Parameter auf die Schnittstelle als eine Variante für übergeben SAFEARRAY wie gezeigt in das Codesegment `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Benutzerdefinierte Parameter enthalten, ein Array von benutzerdefinierten Parametern. Eine VSZ-Datei übergibt benutzerdefinierte Parameter an die IDE. Die Werte hängen von der `Param=` Anweisungen. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).  
  
-   Rückgabewerte für die-Schnittstelle  
  
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
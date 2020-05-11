---
title: Assistentenschnittstelle (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703273"
---
# <a name="wizard-interface-idtwizard"></a>Assistentenschnittstelle (IDTWizard)
Die integrierte Entwicklungsumgebung (IDE) verwendet die <xref:EnvDTE.IDTWizard> Schnittstelle, um mit Assistenten zu kommunizieren. Assistenten müssen diese Schnittstelle implementieren, um in der IDE installiert zu werden.

 Die <xref:EnvDTE.IDTWizard.Execute%2A> Methode ist die einzige <xref:EnvDTE.IDTWizard> Methode, die der Schnittstelle zugeordnet ist. Assistenten implementieren diese Methode, und die IDE ruft die Methode auf der Schnittstelle auf. Das folgende Beispiel zeigt die Signatur der Methode.

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

 Der Startmechanismus ist sowohl für den Assistenten für **neues Projekt** als auch für die Assistenten zum Hinzufügen **neuer Elemente** ähnlich. Um entweder zu starten, rufen Sie die <xref:EnvDTE.IDTWizard> in Dteinternal.h definierte Schnittstelle auf. Der einzige Unterschied besteht in dem Satz von Kontext und benutzerdefinierten Parametern, die an die Schnittstelle übergeben werden, wenn die Schnittstelle aufgerufen wird.

 Die folgenden Informationen <xref:EnvDTE.IDTWizard> beschreiben die Schnittstelle, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Assistenten implementieren müssen, um in der IDE zu arbeiten. Die IDE <xref:EnvDTE.IDTWizard.Execute%2A> ruft die Methode für den Assistenten auf und übergibt sie wie folgt:

- Das DTE-Objekt

     Das DTE-Objekt ist der Stamm des Automatisierungsmodells.

- Das Handle zum Fensterdialogfeld, wie im `hwndOwner ([in] long)`Codesegment gezeigt.

     Der Assistent `hwndOwner` verwendet dies als übergeordnetes Element für das Dialogfeld des Assistenten.

- Kontextparameter, die als Variante für SAFEARRAY an die `[in] SAFEARRAY (VARIANT)* ContextParams`Schnittstelle übergeben werden, wie im Codesegment gezeigt.

     Kontextparameter enthalten ein Array von Werten, die für die Art des assistenten, der gestartet wird, und den aktuellen Status des Projekts spezifisch sind. Die IDE übergibt die Kontextparameter an den Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).

- Benutzerdefinierte Parameter, die als Variante für SAFEARRAY an `[in] SAFEARRAY (VARIANT)* CustomParams`die Schnittstelle übergeben werden, wie im Codesegment gezeigt.

     Benutzerdefinierte Parameter enthalten ein Array benutzerdefinierter Parameter. Eine .vsz-Datei übergibt benutzerdefinierte Parameter an die IDE. Die Werte werden `Param=` durch die Anweisungen bestimmt. Weitere Informationen finden Sie unter [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).

- Rückgabewerte für die Schnittstelle sind

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Weitere Informationen
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

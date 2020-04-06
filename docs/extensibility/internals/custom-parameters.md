---
title: Benutzerdefinierte Parameter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708945"
---
# <a name="custom-parameters"></a>Benutzerdefinierte Parameter
Benutzerdefinierte Parameter steuern den Betrieb eines Assistenten, nachdem ein Assistent gestartet wurde. Eine zugehörige *.vsz-Datei* stellt ein Array von benutzerdefinierten Parametern bereit, die von der integrierten Entwicklungsumgebung (IDE) gepackt und beim Starten des Assistenten als Array von Zeichenfolgen an den Assistenten übergeben werden. Der Assistent analysiert dann das Array von Zeichenfolgen und verwendet die Informationen, um den tatsächlichen Vorgang des Assistenten zu steuern. Auf diese Weise kann ein Assistent die Funktionalität abhängig vom Inhalt der *.vsz-Datei* anpassen.

 Kontextparameter hingegen definieren den Status des Projekts, wenn der Assistent gestartet wird. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).

 Im Folgenden finden Sie ein Beispiel für eine *.vsz-Datei* mit benutzerdefinierten Parametern:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Der Autor der *.vsz-Datei* fügt die Werte der Parameter hinzu. Wenn ein Benutzer im Menü **Datei** **neues Projekt** oder Neues **Element hinzufügen** oder mit der rechten Maustaste auf ein Projekt im **Projektmappen-Explorer**klickt, sammelt die IDE diese Werte in einem Array von Zeichenfolgen. Die IDE ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> die Projektmethode mit dem <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Flagsatz <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> auf, und das Projekt ruft die Methode auf, die für die Ausführung des Assistenten und die Rückgabe des Ergebnisses verantwortlich ist.

 Der Assistent ist dafür verantwortlich, das Array von Zeichenfolgen zu analysieren und entsprechend auf die Zeichenfolgen zu reagieren. Auf diese Weise können Sie durch Implementieren benutzerdefinierter Parameter einen Assistenten erstellen, der eine Vielzahl von Funktionen ausführt. Mit anderen Worten, ein Assistent könnte drei verschiedene *.vsz-Dateien* haben. Jede Datei übergibt verschiedene Sätze benutzerdefinierter Parameter, um das Verhalten des Assistenten in verschiedenen Situationen zu steuern.

 Weitere Informationen finden Sie unter [Wizard (.vsz)-Datei](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Wizarddatei (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

---
title: Kontextparameter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709311"
---
# <a name="context-parameters"></a>Kontextparameter
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der integrierten Entwicklungsumgebung (IDE) können Sie den Dialogfeldern **Neues Projekt,** **Neues Element hinzufügen**oder **Unterprojekt** hinzufügen Assistenten hinzufügen. Die hinzugefügten Assistenten sind im Menü **Datei** verfügbar oder durch Rechtsklick auf ein Projekt im **Projektmappen-Explorer**. Die IDE übergibt Kontextparameter an die Implementierung des Assistenten. Die Kontextparameter definieren den Status des Projekts, wenn die IDE den Assistenten aufruft.

 Die IDE startet Assistenten, <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> indem sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> im Aufruf der IDE an die Methode für das Projekt angibt. Wenn festgelegt, muss das `IVsExtensibility::RunWizardFile` Projekt dazu führen, dass die Methode mithilfe des registrierten Assistentennamens oder der GUID und anderer Kontextparameter ausgeführt wird, die die IDE an sie übergibt.

## <a name="context-parameters-for-new-project"></a>Kontextparameter für neues Projekt

| Parameter | BESCHREIBUNG |
|-------------------------| - |
| `WizardType` | Registrierter Assistenttyp (<xref:EnvDTE.Constants.vsWizardNewProject>) oder die GUID, die den Typ des Assistenten angibt. In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] der Implementierung lautet die GUID für den Assistenten : '0F90E1D0-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Eine Zeichenfolge, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der eindeutige Projektname ist. |
| `LocalDirectory` | Lokaler Speicherort der arbeitsfähigen Projektdateien. |
| `InstallationDirectory` | Verzeichnispfad der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation. |
| `FExclusive` | Boolesche Flagge, die angibt, dass das Projekt offene Lösungen schließen soll. |
| `SolutionName` | Name der Projektmappendatei ohne den Verzeichnisteil oder die *Erweiterung .sln.* Der *.suo-Dateiname* wird `SolutionName`auch mithilfe von erstellt. Wenn es sich bei diesem Argument <xref:EnvDTE._Solution.Create%2A> nicht um eine <xref:EnvDTE._Solution.AddFromTemplate%2A>leere Zeichenfolge handelt, verwendet der Assistent vor dem Hinzufügen des Projekts mit . Wenn es sich bei diesem <xref:EnvDTE._Solution.AddFromTemplate%2A> Namen <xref:EnvDTE._Solution.Create%2A>um eine leere Zeichenfolge handelt, verwenden Sie die verwenden, ohne aufzurufen. |
| `Silent` | Boolesche, die angibt, ob der Assistent im`TRUE`Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( ). |

## <a name="context-parameters-for-add-new-item"></a>Kontextparameter für Neues Element hinzufügen

| Parameter | BESCHREIBUNG |
|-------------------------| - |
| `WizardType` | Registrierter Assistenttyp (<xref:EnvDTE.Constants.vsWizardAddItem>) oder die GUID, die den Typ des Assistenten angibt. In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] der Implementierung lautet die GUID für den Assistenten : '0F90E1D1-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Eine Zeichenfolge, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der eindeutige Projektname ist. |
| `ProjectItems` | Lokaler Speicherort, der funktionierende Projektdateien enthält. |
| `ItemName` | Name des hinzuzufügenden Elements. Dieser Name ist entweder der Standarddateiname oder der Dateiname, den der Benutzer im Dialogfeld **Elemente hinzufügen** eingibt. Der Name basiert auf den Flags, die in der *.vsdir-Datei* festgelegt sind. Der Name kann ein NULL-Wert sein. |
| `InstallationDirectory` | Verzeichnispfad der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation. |
| `Silent` | Boolesche, die angibt, ob der Assistent im`TRUE`Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Kontextparameter für Add Sub Project

| Parameter | BESCHREIBUNG |
|-------------------------| - |
| `WizardType` | Registrierter Assistenttyp (<xref:EnvDTE.Constants.vsWizardAddSubProject>) oder die GUID, die den Typ des Assistenten angibt. In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] der Implementierung lautet die GUID für den Assistenten : '0F90E1D2-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Eine Zeichenfolge, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der eindeutige Projektname ist. |
| `ProjectItems` | Zeigen Sie `ProjectItems` mit dem Zeiger auf die Auflistung, für die der Assistent arbeitet. Dieser Zeiger wird basierend auf der Projekthierarchieauswahl an den Assistenten übergeben. Ein Benutzer wählt in der Regel einen Ordner aus, in den das Element gelegt werden soll, und ruft dann das Dialogfeld **Element hinzufügen** des Projekts auf. |
| `LocalDirectory` | Lokaler Speicherort der arbeitsfähigen Projektdateien. |
| `ItemName` | Name des hinzuzufügenden Elements. Dieser Name ist entweder der Standarddateiname oder der Dateiname, den der Benutzer im Dialogfeld **Elemente hinzufügen** eingibt. Der Name basiert auf den Flags, die in der *.vsdir-Datei* festgelegt sind. Der Name kann ein NULL-Wert sein. |
| `InstallationDirectory` | Verzeichnispfad der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installation. |
| `Silent` | Boolesche, die angibt, ob der Assistent im`TRUE`Hintergrund ausgeführt werden soll, als ob auf **Fertig** stellen geklickt wurde ( ). |

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Wizarddatei (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Kontextparameter zum Starten von Assistenten](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)

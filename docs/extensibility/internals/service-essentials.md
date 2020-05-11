---
title: Service Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705500"
---
# <a name="service-essentials"></a>Dienstgrundlagen
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage stellt einen bestimmten Satz von Schnittstellen für ein anderes VSPackage bereit. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ist selbst eine Sammlung von VSPackages, die Dienste für andere VSPackages bereitstellt.

 Sie können z. B. den SVsActivityLog-Dienst verwenden, um eine IVsActivityLog-Schnittstelle abzusondern, mit der Sie in das Aktivitätsprotokoll schreiben können. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet auch einige integrierte Dienste, die nicht registriert sind. VSPackages kann integrierte oder andere Dienste durch die Bereitstellung einer Dienstüberschreibung ersetzen. Für jeden Dienst ist nur eine Dienstüberschreibung zulässig.

 Dienste sind nicht auffindbarkeitsfähig. Daher müssen Sie die Dienstkennung (SID) eines Dienstes kennen, den Sie nutzen möchten, und Sie müssen wissen, welche Schnittstellen er bereitstellt. Die Referenzdokumentation für den Dienst stellt diese Informationen bereit.

- VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.

- Dienste, die anderen VSPackages zur Verfügung gestellt werden, werden als globale Dienste bezeichnet.

- Dienste, die nur für das VSPackage, das sie implementiert, oder für ein beliebiges Objekt, das sie erstellt werden, verfügbar sind, werden als lokale Dienste bezeichnet.

- Dienste, die integrierte Dienste oder Dienste ersetzen, die von anderen Paketen bereitgestellt werden, werden als Dienstüberschreibungen bezeichnet.

- Dienste oder Dienstüberschreibungen werden bei Bedarf geladen, d. h., der Dienstanbieter wird geladen, wenn der von ihm angebotene Dienst von einem anderen VSPackage angefordert wird.

- Um das Laden auf Anforderung zu unterstützen, registriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ein Dienstanbieter seine globalen Dienste bei . Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen eines Dienstes](../../extensibility/how-to-provide-a-service.md).

- Nachdem Sie einen Dienst erhalten haben, verwenden Sie [QueryInterface](/cpp/atl/queryinterface) (nicht verwalteter Code) oder eine Umwandlung (verwalteter Code), um die gewünschte Schnittstelle abzusuchen, z. B.:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Verwalteter Code bezieht sich auf einen Dienst nach seinem Typ, während nicht verwalteter Code von seiner GUID auf einen Dienst verweist.

- Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein VSPackage geladen wird, wird ein Dienstanbieter an das VSPackage weitergereicht, um dem VSPackage Zugriff auf globale Dienste zu gewähren. Dies wird als "Sitzen" des VSPackage bezeichnet.

- VSPackages können Dienstanbieter für die Objekte sein, die sie erstellen. Ein Formular kann z. B. eine Anforderung für einen Farbdienst [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]an seinen Rahmen senden, der die Anforderung an übergibt.

- Verwaltete Objekte, die tief verschachtelt sind oder <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> überhaupt nicht vorOrt sind, erfordern möglicherweise direkten Zugriff auf globale Dienste.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>GetGlobalService verwenden

Manchmal müssen Sie einen Dienst aus einem Toolfenster oder Einem Steuerelementcontainer abrufen, der nicht standortgebunden ist, oder sie wurden bei einem Dienstanbieter eingerichtet, der den gewünschten Dienst nicht kennt. Sie können z. B. innerhalb eines Steuerelements in das Aktivitätsprotokoll schreiben. Weitere Informationen zu diesen und anderen Szenarien finden Sie unter [Gewusst wie: Fehlerbehebungsdienste](../../extensibility/how-to-troubleshoot-services.md).

Sie können die meisten Visual Studio-Dienste abrufen, indem Sie die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode aufrufen.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>basiert auf einem zwischengespeicherten Dienstanbieter, der zum ersten Mal initialisiert wird, wenn ein von Package abgeleitetes VSPackage standortbasiert ist. Sie müssen garantieren, dass diese Bedingung erfüllt ist, oder für einen NULL-Dienst vorbereitet sein.

Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funktioniert die meiste Zeit korrekt.

- Wenn ein VSPackage einen Dienst bereitstellt, der nur einem anderen VSPackage bekannt ist, wird das VSPackage, das den Dienst anfordert, vor dem VsPackage, das den Dienst bereitstellt, vor Ort installiert.

- Wenn ein Toolfenster von einem VSPackage erstellt wird, wird das VSPackage vor dem Erstellen des Toolfensters erstellt.

- Wenn ein Steuerelementcontainer von einem Von einem VSPackage erstellten Toolfenster gehostet wird, wird das VSPackage vor dem Erstellen des Steuerelementcontainers sited.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>So erhalten Sie einen Dienst in einem Werkzeugfenster oder Steuercontainer

- Fügen Sie diesen Code in den Konstruktor, das Werkzeugfenster oder den Steuercontainer ein:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Dieser Code ruft einen SVsActivityLog-Dienst ab und gibt ihn in eine IVsActivityLog-Schnittstelle um, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Weitere Informationen

- [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)
- [Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md)
- [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Umwandlung](/cpp/cpp/casting)

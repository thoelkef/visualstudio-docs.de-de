---
title: Service Essentials | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e867c9e83bf353e57d75ee611fe1074efcc9cfe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070380"
---
# <a name="service-essentials"></a>Dienstgrundlagen
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist selbst eine Auflistung von VSPackages, die Dienste für andere VSPackages bereitstellt.

 Sie können z. B. der SVsActivityLog-Dienst verwenden, beim Abrufen einer IVsActivityLog-Schnittstelle, die Sie zum Schreiben in das Aktivitätsprotokoll verwenden können. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet außerdem einige integrierte Dienste, die nicht registriert sind. VSPackages können integrierte oder andere Dienste ersetzen Sie dies durch die Bereitstellung von einem Dienst außer Kraft setzen. Nur ein Dienst außer Kraft setzen, ist für jeden Dienst zulässig.

 Dienste verfügen über keine ermittelbarkeit. Aus diesem Grund benötigen Sie die Dienst-ID (SID) eines Diensts, die Sie nutzen möchten, und Sie müssen wissen, welche Schnittstellen es bietet. Die Referenzdokumentation für den Dienst stellt diese Informationen bereit.

- VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.

- Dienste, die anderen VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.

- Dienste, die nur für das VSPackage, das sie implementiert, oder auf ein beliebiges Objekt damit erstellten verfügbar sind, werden als lokale Dienste bezeichnet.

- Dienste, die integrierten Dienste oder Dienste von anderen Paketen zu ersetzen, werden als dienstüberschreibungen bezeichnet.

- Dienste oder dienstüberschreibungen, bei Bedarf geladen werden, die der Dienstanbieter ist, also geladen, wenn der bereitgestellte Dienst von einem anderen VSPackage angefordert wird.

- Um das bedarfsgesteuerte Laden zu unterstützen, registriert ein Dienstanbieter seine globalen Dienste mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Geben Sie einen Dienst](../../extensibility/how-to-provide-a-service.md).

- Verwenden Sie nach dem Erwerb eines Diensts [QueryInterface](/cpp/atl/queryinterface) (nicht verwaltetem Code) oder umwandeln (verwalteter Code), um die gewünschte Schnittstelle, z. B. zu erhalten:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Verwalteter Code verweist auf einen Dienst anhand des Typs, auf, während an einen Dienst durch ihre GUID nicht verwalteter Code bezeichnet.

- Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt ein VSPackage, übergibt einen Dienstanbieter für dem VSPackage die VSPackage-Zugriff auf globale Dienste gewähren. Dies wird als "Positionierung" VSPackage bezeichnet.

- VSPackages kann es sich um Dienstanbieter für die Objekte sein, die sie erstellen. Ein Formular könnte z. B. eine Anforderung für einen Dienst für die Farbe an die Rahmen, der der Anforderung übergeben kann senden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Verwaltete Objekte, die tief verschachtelt sind, oder überhaupt nicht positioniert können aufgerufen werden <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> für direkten Zugriff auf globale Dienste.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Verwenden von GetGlobalService

Manchmal müssen Sie zum Abrufen eines Diensts aus einem Toolfenster oder steuern, Container, der ist nicht positioniert wurde, andernfalls ist bei einem Dienstanbieter, der nicht über den Dienst kennt gewünschten positioniert wurde. Beispielsweise empfiehlt es sich zum Schreiben in das Aktivitätsprotokoll in einem Steuerelement aus. Weitere Informationen zu diesen und andere Szenarien finden Sie unter [Vorgehensweise: Problembehandlung bei Services](../../extensibility/how-to-troubleshoot-services.md).

Sie können die meisten Visual Studio-Dienste abrufen, durch Aufrufen der statischen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basiert auf einem zwischengespeicherten Dienst Anbieter, der zum ersten Mal initialisiert wird jedem VSPackage aus dem Paket abgeleitet positioniert ist. Sie müssen sicherstellen, dass diese Bedingung erfüllt ist, andernfalls ein null-Dienst vorbereitet sein.

Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ordnungsgemäß in den meisten Fällen funktioniert.

- Wenn eine VSPackage ein Dienst, der nur auf einem anderen VSPackage bezeichnet bereitstellt, ist das VSPackage, die die Dienste anfordern positioniert, vor dem VSPackage, das, dass der Dienst geladen werden.

- Wenn von einem VSPackage ein Toolfenster erstellt wird, ist das VSPackage positioniert, bevor das Toolfenster erstellt wird.

- Wenn ein Toolfenster erstellt, die von einem VSPackage ein Steuerelementcontainer gehostet wird, ist das VSPackage positioniert, bevor der Steuerelement-Container erstellt wird.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Um einen Dienst in einem Werkzeugcontainer Fensters oder Steuerelements zu erhalten.

- Fügen Sie diesen Code im Konstruktor, Toolfenster oder Control-Containers an:

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

    Dieser Code Ruft einen Dienst SVsActivityLog und wandelt ihn in eine IVsActivityLog-Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Siehe auch

- [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)
- [Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md)
- [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Umwandlung](/cpp/cpp/casting)
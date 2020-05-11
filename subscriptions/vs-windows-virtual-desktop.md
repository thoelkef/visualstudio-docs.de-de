---
title: Microsoft Windows Virtual Desktop-Vorteil in Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Hier erfahren Sie, wie Sie Microsoft Windows Virtual Desktop über Ihr Visual Studio-Abonnement nutzen können.
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649738"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Zugriff auf Windows Virtual Desktop in Abonnements 
Visual Studio-Abonnenten können nun ihr Azure DevTest-Einzelguthaben für Microsoft Windows Virtual Desktop-Dienste verwenden.  
Bei Windows Virtual Desktop handelt es sich um einen umfassenden Dienst für die Desktop- und App-Virtualisierung, der in der Cloud ausgeführt wird. Dieser Dienst ist die einzige virtuelle Desktopinfrastruktur, die vereinfachte Verwaltung, Windows 10 mit mehreren Sitzungen, Optimierungen für Office 365 ProPlus sowie Unterstützung für Umgebungen von Remotedesktopdiensten bietet. Stellen Sie Ihre Windows-Desktops und -Apps innerhalb weniger Minuten bereit, und skalieren Sie diese. Außerdem profitieren Sie von integrierten Sicherheits- und Konformitätsfeatures.
Windows Virtual Desktop in Azure ermöglicht Folgendes:
- Einrichten einer Windows 10-Bereitstellung mit mehreren Sitzungen, die eine vollständige Windows 10-Umgebung mit Skalierbarkeit bietet
- Virtualisieren von Office 365 ProPlus und Optimieren der Ausführung in virtuellen Szenarien mit mehreren Benutzern
- Bereitstellen virtueller Windows 7-Desktops mit kostenlosen erweiterten Sicherheitsupdates
- Verwenden bereits vorhandener Remotedesktopdienste (Remote Desktop Services, RDS) und Windows Server-Desktops/-Apps auf einem beliebigen Computer
- Virtualisieren von Desktops und Apps
- Verwalten Sie Windows 10-, Windows Server- und Windows 7-Desktops und -Apps über eine vereinheitlichte Verwaltungsbenutzeroberfläche. Weitere Informationen darüber, was Ihnen mit Windows Virtual Desktop ermöglicht wird, finden Sie in diesem [Einführungsvideo](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Verwenden von Windows Virtual Desktop mit Azure 
Visual Studio-Abonnenten verfügen nun über mehrere Möglichkeiten, um Azure-Abonnements für die Zahlung für Windows Virtual Desktop-Dienste zu verwenden:
- [Einzelguthaben für Azure DevTest:](vs-azure.md)  Abonnenten, die im Rahmen ihrer Abonnements Azure DevTest-Einzelguthaben erhalten, können dieses Guthaben dazu verwenden, für Windows Virtual Desktop-Dienste zu zahlen.  Der Betrag des monatlichen Guthabens hängt von der Abonnementstufe ab.
- [Azure DevTest-Abonnements mit nutzungsbasierter Bezahlung:](vs-azure-payg.md)  Sie können Azure-Abonnements erstellen und ein Zahlungsinstrument angeben, um nahtlos für Ihre Nutzung von Windows Virtual Desktop zu zahlen. 
- [Azure Enterprise Agreement-DevTest-Angebot:](azure-ea-devtest.md)  Mit diesem Angebot können Abonnenten mit Enterprise Agreement für Windows Virtual Desktop in Azure zu reduzierten Tarifen zahlen. 

## <a name="requirements"></a>Anforderungen
Für Windows Virtual Desktop ist eine Azure Active Directory-Instanz erforderlich, in die VMs eingebunden werden.  Benutzer müssen Mitglieder dieser Azure AD-Instanz sein.  Für die Implementierung von Azure AD stehen Ihnen zwei Optionen zur Verfügung:
- Azure AD-Verzeichnisdienste:  Für die meisten Benutzer erweist sich diese Option bei der Implementierung als einfacher.
- Ein virtueller Computer, der eine Domänencontrollerpromo ausführt:  Diese Option erfordert mehr Aufwand für die Einrichtung, bietet in den meisten Fällen jedoch geringere Betriebskosten.
Eine vollständige Liste der Voraussetzungen für die Verwendung von Windows Virtual Desktop finden Sie auf der [Übersichtsseite zu Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements). 

## <a name="get-started"></a>Erste Schritte 
Wenn Sie alle Voraussetzungen erfüllen, sollten Sie einige Aktionen durchführen, um die Implementierung einzurichten.  Informationen zu den ersten Schritten finden Sie in den folgenden Tutorials:
- [Erstellen eines Windows Virtual Desktop-Mandanten](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Erstellen eines Hostpools über das Azure-Portal](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)
- [Verwalten von App-Gruppen für Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>Berechtigung
| Abonnementstufe                                                 |     Channels                                            | Vorteil                                                          | Erneuerbar?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Verfügbar|  Ja          |
| Visual Studio Enterprise mit GitHub Enterprise  | VL | Verfügbar|  Ja          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Verfügbar                                                             |  Ja             |
| Visual Studio Professional mit GitHub Enterprise | VL                                       | Verfügbar                                        |  Ja           |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Verfügbar|  Ja          |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Verfügbar                                         |  Ja          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Nicht verfügbar  | Nicht zutreffend |
| Visual Studio Enterprise, Visual Studio Professional (Cloudabonnement mit monatlicher Laufzeit) | Azure | Nicht verfügbar | Nicht zutreffend |

<sup>1</sup> *Enthält:  Not for Resale (NFR), FTE, Most Valuable Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> In Cloud-Abonnements enthaltene Jahresabonnements von Visual Studio Professional und Visual Studio Enterprise werden von Microsoft nicht mehr angeboten. An den vorhandenen Funktionen und der Möglichkeit, Abonnements zu erneuern, erhöhen, verringern oder zu kündigen, wird sich nichts ändern. Neuen Kunden wird empfohlen, die verschiedenen Optionen für den Erwerb von Visual Studio unter [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) zu vergleichen.

Sie wissen nicht genau, welches Abonnement Sie verwenden?  Stellen Sie eine Verbindung mit [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) her, um alle Abonnements anzuzeigen, die Ihrer E-Mail-Adresse zugewiesen sind. Wenn nicht alle Ihrer Abonnements angezeigt werden, sind möglicherweise einige Abonnements einer anderen E-Mail-Adresse zugewiesen.  Sie müssen sich mit der entsprechenden E-Mail-Adresse anmelden, um diese Abonnements anzuzeigen.

## <a name="see-also"></a>Siehe auch
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Nächste Schritte
-   Informationen zum Erwerben von Visual Studio-Abonnements finden Sie unter:
     - [Preise im Einzelhandel](https://visualstudio.microsoft.com/vs/pricing/) im Microsoft Store
     - [Programme für die Volumenlizenzierung](https://www.microsoft.com/licensing/default)
-   Weitere Informationen zu [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview) 

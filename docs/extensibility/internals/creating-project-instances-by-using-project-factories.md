---
title: Erstellen von Projektinstanzen mithilfe von Projektfabriken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709064"
---
# <a name="create-project-instances-by-using-project-factories"></a>Erstellen von Projektinstanzen mithilfe von Projektfabriken
Projekttypen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden eine *Projektfactory,* um Instanzen von Projektobjekten zu erstellen. Eine Projektfactory ähnelt einer Standardklassenfabrik für kokreierbare COM-Objekte. Projektobjekte sind jedoch nicht kocreatable. sie können nur mit einer Projektfactory erstellt werden.

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ruft die in Ihrem VSPackage implementierte Projektfactory auf, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wenn ein Benutzer ein vorhandenes Projekt lädt oder ein neues Projekt in erstellt. Das neue Projektobjekt stellt der IDE genügend Informationen zum Auffüllen des **Projektmappen-Explorers**zur Verfügung. Das neue Projektobjekt stellt auch die erforderlichen Schnittstellen für die Unterstützung aller relevanten UI-Aktionen bereit, die von der IDE initiiert wurden.

 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> die Schnittstelle in einer Klasse in Ihrem Projekt implementieren. In der Regel befindet es sich in einem eigenen Modul.

 Projekte, die die Aggregation durch einen Besitzer unterstützen, müssen einen Besitzerschlüssel in ihrer Projektdatei beibehalten. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> die Methode für ein Projekt mit einem Besitzerschlüssel aufgerufen wird, konvertiert das eigene `CreateProject` Projekt seinen Besitzerschlüssel in eine Projektfactory-GUID und ruft dann die Methode in dieser Projektfactory auf, um die eigentliche Erstellung zu erledigen.

## <a name="create-an-owned-project"></a>Erstellen eines eigenen Projekts
 Ein Besitzer erstellt ein eigenes Projekt in zwei Phasen:

1. Durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> der Methode. Dadurch besteht die Möglichkeit, ein aggregiertes Projektobjekt basierend `IUnknown`auf dem Eingabecontrolling zu erstellen. Das eigene Projekt `IUnknown` übergibt das innere und das aggregierte Objekt an das Eigentümerprojekt zurück. Dies gibt dem eigenen Projekt `IUnknown`die Möglichkeit, die innere zu speichern.

2. Durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> der Methode. Das eigene Projekt führt alle Instanziierungen durch, `IVsProjectFactory::CreateProject` wenn diese Methode aufgerufen wird, anstatt aufzurufen, wie dies bei Projekten der Fall wäre, die nicht im Besitz sind. Die `VSOWNEDPROJECTOBJECT` Eingabeenumeration ist in der Regel das aggregierte Eigene Projekt. Das im Besitz befindliche Projekt kann diese Variable verwenden, um zu bestimmen, ob das Projektobjekt bereits erstellt wurde (Cookie entspricht nicht NULL) oder erstellt werden muss (Cookie gleich NULL).

   Projekttypen werden durch eine eindeutige Projekt-GUID identifiziert, ähnlich der CLSID eines kocreatable COM-Objekts. In der Regel verarbeitet eine Projektfactory das Erstellen von Instanzen eines einzelnen Projekttyps, obwohl es möglich ist, dass eine Projektfactory mehr als eine Projekttyp-GUID verarbeitet.

   Projekttypen sind einer bestimmten Dateinamenerweiterung zugeordnet. Wenn ein Benutzer versucht, eine vorhandene Projektdatei zu öffnen, oder versucht, ein neues Projekt durch Klonen einer Vorlage zu erstellen, verwendet die IDE die Erweiterung in der Datei, um die entsprechende Projekt-GUID zu ermitteln.

   Sobald die IDE bestimmt, ob sie ein neues Projekt erstellen oder ein vorhandenes Projekt eines bestimmten Typs öffnen muss, verwendet die IDE die Informationen in der Systemregistrierung unter **[HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio-Projekte],** um herauszufinden, welches VSPackage die erforderliche Projektfactory implementiert. Die IDE lädt dieses VSPackage. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> der Methode muss das VSPackage seine Projektfactory <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> bei der IDE registrieren, indem es die Methode aufruft.

   Die primäre Methode `IVsProjectFactory` der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>Schnittstelle ist , die zwei Szenarien behandeln sollte: Das Öffnen eines vorhandenen Projekts und das Erstellen eines neuen Projekts. Die meisten Projekte speichern ihren Projektstatus in einer Projektdatei. In der Regel werden neue Projekte erstellt, indem `CreateProject` eine Kopie der Vorlagendatei an die Methode übergeben und dann geöffnet wird. Vorhandene Projekte werden instanziiert, indem die `CreateProject` projektdatei direkt an die Methode übergeben wird. Die `CreateProject` Methode kann dem Benutzer bei Bedarf zusätzliche UI-Features anzeigen.

   Ein Projekt kann auch keine Dateien verwenden und stattdessen seinen Projektstatus in einem anderen Speichermechanismus als dem Dateisystem speichern, z. B. einer Datenbank oder einem Webserver. In diesem Fall ist der an `CreateProject` die Methode übergebene Dateinamenparameter eigentlich kein Dateisystempfad, sondern eine eindeutige Zeichenfolge – eine URL –, um die Projektdaten zu identifizieren. Sie müssen die Vorlagendateien, an `CreateProject` die übergeben wird, nicht kopieren, um die entsprechende Auszuführensequenz auszulösen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Checkliste: Neue Projekttypen erstellen](../../extensibility/internals/checklist-creating-new-project-types.md)

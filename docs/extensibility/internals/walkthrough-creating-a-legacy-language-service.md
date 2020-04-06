---
title: 'Exemplarische Vorgehensweise: Erstellen eines Legacy-Sprachdienstes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703688"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts
Die Verwendung der MPF-Sprachklassen (Managed Package [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Framework) zum Implementieren eines Sprachdienstes in ist einfach. Sie benötigen ein VSPackage, um den Sprachdienst, den Sprachdienst selbst und einen Parser für Ihre Sprache zu hosten.

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Stellen für die VSPackage-Projektvorlage
 Die Visual Studio-Paketprojektvorlage befindet sich an drei verschiedenen Vorlagenpositionen im Dialogfeld **Neues Projekt:**

1. Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.

2. Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.

3. Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.

### <a name="create-a-vspackage"></a>Erstellen eines VSPackage

1. Erstellen Sie ein neues VSPackage mit der Visual Studio Package-Projektvorlage.

    Wenn Sie einem vorhandenen VSPackage einen Sprachdienst hinzufügen, überspringen Sie die folgenden Schritte, und wechseln Sie direkt zur Prozedur "Erstellen der Sprachdienstklasse".

2. Geben Sie MyLanguagePackage für den Namen des Projekts ein, und klicken Sie auf **OK**.

    Sie können jeden beliebigen Namen verwenden. Bei diesen hier beschriebenen Verfahren wird MyLanguagePackage als Name angenommen.

3. Wählen [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Sie als Sprache und option zum Generieren einer neuen Schlüsseldatei aus. Klicken Sie auf **Weiter**.

4. Geben Sie die entsprechenden Unternehmens- und Paketinformationen ein. Klicken Sie auf **Weiter**.

5. Wählen Sie **Menübefehl**. Klicken Sie auf **Weiter**.

    Wenn Sie keine Codeausschnitte unterstützen möchten, können Sie einfach auf Fertig stellen klicken und den nächsten Schritt ignorieren.

6. Geben Sie **Insert Snippet** `cmdidInsertSnippet` als **Befehlsnamen** und für die **Befehls-ID ein.** Klicken Sie auf **Fertig stellen**.

    Der **Befehlsname** und die **Befehls-ID** können sein, was Sie wollen, dies sind nur Beispiele.

### <a name="create-the-language-service-class"></a>Erstellen der Sprachdienstklasse

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das MyLanguagePackage-Projekt, wählen **Sie Hinzufügen**, **Referenz**aus, und wählen Sie dann die Schaltfläche Neue **Referenz hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Referenz hinzufügen** die Option **Microsoft.VisualStudio.Package.LanguageService** auf der Registerkarte **.NET aus,** und klicken Sie auf **OK**.

     Dies muss nur einmal für das Sprachpaketprojekt erfolgen.

3. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **Hinzufügen**, **Klasse**.

4. Stellen Sie sicher, dass **Die Option Klasse** in der Vorlagenliste ausgewählt ist.

5. Geben Sie **MyLanguageService.cs** für den Namen der Klassendatei ein, und klicken Sie auf **Hinzufügen**.

     Sie können jeden beliebigen Namen verwenden. Diese hier beschriebenen Verfahren gehen als Name an. `MyLanguageService`

6. Fügen Sie in der `using` Datei MyLanguageService.cs die folgenden Direktiven hinzu.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Ändern `MyLanguageService` Sie die Klasse, <xref:Microsoft.VisualStudio.Package.LanguageService> um sie von der Klasse abzuleiten:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Positionieren Sie den Cursor auf "LanguageService" und wählen Sie im Menü **Bearbeiten**, **IntelliSense** die Option **Abstrakte Klasse implementieren**aus. Dadurch werden die minimal erforderlichen Methoden zum Implementieren einer Sprachdienstklasse hinzugefügt.

9. Implementieren Sie die abstrakten Methoden, wie unter [Implementieren eines Legacy-Sprachdienstes](../../extensibility/internals/implementing-a-legacy-language-service2.md)beschrieben.

### <a name="register-the-language-service"></a>Registrieren des Sprachdienstes

1. Öffnen Sie die MyLanguagePackagePackage.cs `using` Datei, und fügen Sie die folgenden Direktiven hinzu:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registrieren Sie Ihre Sprachdienstklasse, wie unter [Registrieren eines Legacy-Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service1.md)beschrieben. Dazu gehören die ProvideXX-Attribute und die Abschnitte "Proffering the Language Service". Verwenden Sie MyLanguageService, wenn in diesem Thema TestLanguageService verwendet wird.

### <a name="the-parser-and-scanner"></a>Der Parser und Scanner

1. Implementieren Sie einen Parser und Scanner für Ihre Sprache, wie unter [Legacy Language Service Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)beschrieben.

     Wie Sie Ihren Parser und Scanner implementieren, liegt ganz bei Ihnen und liegt außerhalb des Rahmens dieses Themas.

## <a name="language-service-features"></a>Sprachdienstfunktionen
 Um jedes Feature im Sprachdienst zu implementieren, leiten Sie in der Regel eine Klasse aus der entsprechenden MPF-Sprachdienstklasse ab, implementieren bei Bedarf alle abstrakten Methoden und überschreiben die entsprechenden Methoden. Welche Klassen Sie erstellen und/oder daraus ableiten, hängt von den Features ab, die Sie unterstützen möchten. Diese Features werden in [Den Legacy Language Service Features](../../extensibility/internals/legacy-language-service-features1.md)ausführlich erläutert. Das folgende Verfahren ist der allgemeine Ansatz zum Ableiten einer Klasse aus den MPF-Klassen.

#### <a name="deriving-from-an-mpf-class"></a>Ableiten aus einer MPF-Klasse

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **Hinzufügen**, **Klasse**.

2. Stellen Sie sicher, dass **Die Option Klasse** in der Vorlagenliste ausgewählt ist.

     Geben Sie einen geeigneten Namen für die Klassendatei ein, und klicken Sie auf **Hinzufügen**.

3. Fügen Sie in der neuen `using` Klassendatei die folgenden Direktiven hinzu.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Ändern Sie die Klasse, um von der gewünschten MPF-Klasse abzuleiten.

5. Fügen Sie einen Klassenkonstruktor hinzu, der mindestens die gleichen Parameter wie der Konstruktor der Basisklasse annimmt, und übergeben Sie die Konstruktorparameter an den Basisklassenkonstruktor.

     Der Konstruktor für eine von der <xref:Microsoft.VisualStudio.Package.Source> Klasse abgeleitete Klasse könnte z. B. wie folgt aussehen:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Wählen Sie im Menü **Bearbeiten**, **IntelliSense** Die Option **Abstrakte Klasse implementieren** aus, wenn die Basisklasse über abstrakte Methoden verfügt, die implementiert werden müssen.

7. Positionieren Sie andernfalls die Einstelle innerhalb der Klasse, und geben Sie die Methode ein, die überschrieben werden soll.

     Geben Sie `public override` beispielsweise ein, um eine Liste aller Methoden anzuzeigen, die in dieser Klasse überschrieben werden können.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

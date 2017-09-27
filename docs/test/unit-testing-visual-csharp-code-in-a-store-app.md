---
title: Komponententest von Visual C#-Code in einer Store-App | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 19
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 768dd5253edac137c50ced5bf524bcc1fdd7f6da
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Unittests von Visual C#-Code in einer Store-App
Dieses Thema beschreibt eine Möglichkeit zum Erstellen von Komponententests für eine Visual C#-Klasse in einer Windows Store-App. Die Klasse "Rooter" implementiert eine Funktion zum näherungsweisen Berechnen der Quadratwurzel einer vorgegebenen Zahl, und zwar in einer Weise, die entfernt an Grenzwertberechnungen in der Analysis erinnert. Von der Mathematik-App kann diese Funktion dann verwendet werden, um Benutzern zu zeigen, wie interessant und unterhaltsam Mathematik sein kann.  
  
 In diesem Thema wird gezeigt, wie Komponententests als erster Schritt in der Entwicklung verwendet werden. Bei dieser Vorgehensweise schreiben Sie zuerst eine Testmethode, die ein bestimmtes Verhalten in Ihrem Testsystem überprüft. Anschließend schreiben Sie den Code, der im Test erfolgreich ist. Durch das Ändern der Reihenfolge bei den folgenden Prozeduren, können Sie diese Strategie umkehren und zuerst den zu testenden Code und anschließend die Komponententests schreiben.  
  
 In diesem Thema werden auch eine einzelne Visual Studio-Projektmappe und separate Projekte für die zu testenden Komponententests und DLLs erstellt. Sie können die Komponententests auch direkt in das DLL-Projekt einfügen, oder Sie können separate Lösungen für die Komponententests und die DLL erstellen.  
  
> [!NOTE]
>  Visual Studio-Community, Enterprise und Professional stellen zusätzliche Funktionen für Komponententests bereit.  
>   
>  -   Sie können ein beliebiges Drittanbieter- und Open Source-Framework für Komponententest verwenden, mit dem ein Add-On-Adapter für den Microsoft-Test-Explorer erstellt wurde. Sie können auch Codeabdeckungsinformationen für die Tests analysieren und anzeigen.  
> -   Führen Sie Ihre Tests nach jedem Build aus.  
> -   VS Enterprise enthält auch Microsoft Fakes, ein Isolationsframework für verwalteten Code, mit dem Sie Ihre Tests auf den eigenen Code ausrichten können, indem Sie Testcode für System- und Drittanbieterfunktionalität ersetzen.  
>   
>  Weitere Informationen finden Sie unter [Überprüfen von Code mithilfe von Komponententests](http://msdn.microsoft.com/library/dd264975.aspx) in der MSDN Library.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Erstellen der Projektmappe und des Komponententestprojekts](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Sicherstellen, dass die Tests im Test-Explorer ausgeführt werden](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Hinzufügen der Klasse „Rooter“ zu dem Projekt „Mathematik“](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Verknüpfen des Testprojekts mit dem App-Projekt](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Tests iterativ steigern und erfolgreich abschließen](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Debuggen eines fehlgeschlagenen Tests](#BKMK_Debug_a_failing_test)  
  
 [Umgestaltung des Codes](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Erstellen der Projektmappe und des Komponententestprojekts  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** aus, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Installiert**, erweitern Sie **Visual C#**, und wählen Sie **Windows Store** aus. Wählen Sie dann in der Liste der Projektvorlagen **Leere App** aus.  
  
3.  Nennen Sie das Projekt `Maths`, und stellen Sie sicher, dass **Projektmappenverzeichnis erstellen** ausgewählt ist.  
  
4.  Wählen Sie im Projektmappen-Explorer den Projektmappenname aus. Wählen Sie anschließend aus dem Kontextmenü **Hinzufügen** und dann **Neues Projekt** aus.  
  
5.  Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Installiert**, erweitern Sie **Visual C#**, und wählen Sie **Windows Store** aus. Wählen Sie dann **Komponententestbibliothek (Windows Store-Apps)** aus der Liste der Projektvorlagen aus.  
  
     ![Erstellen Sie das Komponententestprojekt](../test/media/ute_cs_windows_createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")  
  
6.  Öffnen Sie UnitTest1.cs im Visual Studio-Editor.  
  
    ```csharp  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Hinweis:  
  
    1.  Jeder Test wird durch die `[TestMethod]`-Verwendung definiert. Eine Testmethode muss den Wert "void" zurückgeben und darf keine Parameter haben.  
  
    2.  Testmethoden müssen in einer Klasse enthalten sein, die durch das `[TestClass]`-Attribut ergänzt wird.  
  
         Wenn die Tests ausgeführt werden, wird eine Instanz jeder Testklasse erstellt. Die Testmethoden werden in einer nicht vorgegebenen Reihenfolge aufgerufen.  
  
    3.  Sie können spezielle Methoden definieren, die vor und nach jedem Modul, jeder Klasse oder Methode aufgerufen werden. Weitere Informationen finden Sie unter [Verwenden von Microsoft.VisualStudio.TestTools.UnitTesting-Membern in Komponententests](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) in der MSDN Library.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Sicherstellen, dass die Tests im Test-Explorer ausgeführt werden  
  
1.  Fügen Sie einen Testcode in `TestMethod1` der Datei **UnitTest1.cs** hinzu.  
  
    ```csharp  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Beachten Sie, dass die `Assert` -Klasse mehrere statische Methoden zur Verfügung stellt, die Sie verwenden können, um Ergebnisse in den Testmethoden zu überprüfen.  
  
2.  Wählen Sie im Menü **Test** die Option **Ausführen** und dann **Alle ausführen** aus.  
  
     Das Testprojekt wird erstellt und ausgeführt. Das Test-Explorer-Fenster wird angezeigt, und der Test wird unter **Bestandene Tests** aufgeführt. Unten im Fenster im Bereich "Zusammenfassung" werden weitere Informationen über den ausgewählten Test angezeigt.  
  
     ![Test-Explorer](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Hinzufügen der Klasse „Rooter“ zu dem Projekt „Mathematik“  
  
1.  Wählen Sie im Projektmappen-Explorer den Projektname **Mathematik**. Wählen Sie im Kontextmenü **Hinzufügen** und dann **Klasse** aus.  
  
2.  Benennen Sie die Klassendatei `Rooter.cs`  
  
3.  Fügen Sie der Rooter-Klassendatei **Rooter.cs** den folgenden Code hinzu:  
  
    ```csharp  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     Die `Rooter`-Klasse deklariert einen Konstruktor und die `SqareRoot`-Abschätzermethode.  
  
4.  Die `SqareRoot`-Methode ist nur eine minimale Implementierung, die gerade ausreicht, um die Grundstruktur des Testsetups zu testen.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Verknüpfen des Testprojekts mit dem App-Projekt  
  
1.  Fügen Sie dem RooterTests-Projekt einen Verweis auf die Mathematik-App hinzu.  
  
    1.  Wählen Sie im Projektmappen-Explorer das Projekt **RooterTests** aus, und wählen Sie dann im Kontextmenü die Option **Verweis hinzufügen** aus.  
  
    2.  Erweitern Sie im Dialogfeld **Verweis hinzufügen - RooterTests** den Eintrag **Projektmappe**, und wählen Sie **Projekte** aus. Wählen Sie dann das Element **Mathematik** aus.  
  
         ![Einen Verweis zum Projekt „Maths“ hinzufügen](../test/media/ute_cs_windows_addreference.png "UTE_Cs_windows_AddReference")  
  
2.  Fügen Sie der Datei "UnitTest1.cs" eine using-Anweisung hinzu:  
  
    1.  Öffnen Sie **UnitTest1.cs**.  
  
    2.  Fügen Sie diesen Code unter der Zeile `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` hinzu:  
  
        ```csharp  
        using Maths;  
        ```  
  
3.  Fügen Sie einen Test hinzu, der die Funktion "Rooter" verwendet. Fügen Sie **unittest1.cpp** den folgenden Code hinzu:  
  
    ```csharp  
    [TestMethod]  
    public void BasicTest()  
    {  
        Maths.Rooter rooter = new Rooter();  
        double expected = 0.0;  
        double actual = rooter.SquareRoot(expected * expected);  
        double tolerance = .001;  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
  
    ```  
  
4.  Erstellen Sie die Projektmappe.  
  
     Der neue Test wird im Test-Explorer im Knoten **Nicht ausgeführte Tests** angezeigt.  
  
5.  Wählen Sie im Test-Explorer **Alle ausführen**aus.  
  
     ![BasicTest bestanden](../test/media/ute_cpp_testexplorer_basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
 Sie haben den Test und die Codeprojekte eingerichtet und überprüft, dass Sie Tests ausführen können, die Funktionen im Codeprojekt ausführen. Jetzt können Sie beginnen, echte Tests und Code zu schreiben.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Die Tests iterativ steigern und erfolgreich abschließen  
  
1.  Fügen Sie einen neuen Test hinzu:  
  
    ```csharp  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  Es wird empfohlen, keine Tests zu ändern, die erfolgreich abgeschlossen wurden. Fügen Sie stattdessen einen neuen Test hinzu, aktualisieren Sie den Code, damit der Test erfolgreich ist, und fügen Sie dann einen weiteren Test hinzu, usw.  
    >   
    >  Wenn Benutzer ihre Anforderungen ändern, deaktivieren Sie die Tests, die nicht mehr richtig sind. Schreiben Sie neue Tests und führen Sie diese jeweils nacheinander auf dieselbe inkrementelle Weise durch.  
  
2.  Wählen Sie im Test-Explorer **Alle ausführen**aus.  
  
3.  Der Test schlägt fehl.  
  
     ![Fehler beim RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Überprüfen Sie unmittelbar nach dem Schreiben eines Tests, dass er fehlschlägt. Dadurch können Sie vermeiden, dass Sie einen Test schreiben, bei dessen Ausführung nie ein Fehler auftritt.  
  
4.  Erweitern Sie den Code unter dem Test, damit der neue Test erfolgreich ist. Ändern Sie die `SqareRoot`-Funktion in **Rooter.cs** zu Folgendem:  
  
    ```csharp  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  Erstellen Sie die Projektmappe, und wählen Sie dann im Test-Explorer **Alle ausführen**aus.  
  
     Alle drei Tests sind jetzt erfolgreich.  
  
> [!TIP]
>  Entwickeln Sie Code, indem Sie währenddessen Tests hinzufügen. Stellen Sie sicher, dass alle Tests nach jeder Iteration erfolgreich sind.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Einen nicht bestandenen Test debuggen  
  
1.  Fügen Sie einen anderen Test zu **UnitTest1.cpp** hinzu:  
  
    ```csharp  
    // Verify that negative inputs throw an exception.  
    [TestMethod]  
    public void NegativeRangeTest()  
    {  
        string message;  
        Rooter rooter = new Rooter();  
        for (double v = -0.1; v > -3.0; v = v - 0.5)  
        {  
            try  
            {  
                // Should raise an exception:  
                double actual = rooter.SquareRoot(v);  
  
                message = String.Format("No exception for input {0}", v);  
                Assert.Fail(message);  
            }  
            catch (ArgumentOutOfRangeException ex)  
            {  
                continue; // Correct exception.  
            }  
            catch (Exception e)  
            {  
                message = String.Format("Incorrect exception for {0}", v);  
                Assert.Fail(message);  
            }  
        }  
    }  
  
    ```  
  
2.  Wählen Sie im Test-Explorer **Alle ausführen**aus.  
  
     Der Test schlägt fehl. Wählen Sie den Testnamen im Test-Explorer aus. Die Assertation, bei der ein Fehler aufgetreten ist, wird gekennzeichnet. Die Fehlermeldung wird im Detailbereich vom Test-Explorer angezeigt.  
  
     ![Fehler bei NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3.  Um zu sehen, warum der Test nicht erfolgreich war, führen Sie schrittweise die Funktion aus:  
  
    1.  Legen Sie einen Haltepunkt am Anfang der `SquareRoot`-Funktion fest.  
  
    2.  Wählen Sie im Kontextmenü des nicht erfolgreichen Tests **Ausgewählte Tests debuggen**.  
  
         Wenn die Ausführung am Haltepunkt angehalten wird, führen Sie den Code schrittweise aus.  
  
    3.  Fügen Sie Code zur Rooter-Methode hinzu, um die Ausnahme zu erfassen:  
  
        ```csharp  
        public double SquareRoot(double x)  
        {  
            if (x < 0.0)  
            {  
                throw new ArgumentOutOfRangeException();  
        }  
  
        ```  
  
    1.  Wählen Sie im Test-Explorer **Alle ausführen** aus, um die korrigierte Methode zu testen und zu überprüfen, dass Sie keine Regression eingeführt haben.  
  
 Alle Tests sind nun erfolgreich.  
  
 ![Alle Tests bestanden](../test/media/ute_ult_alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Umgestalten des Codes  
 **Vereinfachen Sie die zentrale Berechnung in der SquareRoot-Funktion:**  
  
1.  Ändern Sie die Ergebnisimplementierung.  
  
    ```csharp  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Wählen Sie **Alle ausführen** aus, um die umgestaltete Methode zu testen und zu überprüfen, dass Sie keine Regression eingeführt haben.  
  
> [!TIP]
>  Mit einem stabilen Satz guter Komponententests haben Sie mehr Gewissheit, dass Sie beim Ändern des Codes keine Fehler eingeführt haben.  
  
 **Gestalten Sie den Testcode um, um doppelten Code zu vermeiden.**  
  
 Die `RangeTest`-Methode weist dem Nenner der Toleranzvariablen, die in der `Assert`-Methode verwendet wird, vordefinierten Code zu. Wenn Sie zusätzliche Tests hinzufügen möchten, in denen die gleiche Toleranzberechnung zur Anwendung kommt, können Fehler auftreten, wenn ein vordefinierter Wert an mehreren Speicherorten verwendet wird.  
  
1.  Fügen Sie eine private Methode zur Unit1Test-Klasse hinzu, um den Toleranzwert zu berechnen und anschließend stattdessen diese Methode aufzurufen.  
  
    ```csharp  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Wählen Sie **Alle ausführen** aus, um die umgestaltete Methode zu testen und zu überprüfen, dass Sie keinen Fehler eingeführt haben.  
  
> [!NOTE]
>  Wenn Sie eine Hilfsmethode zu einer Testklasse hinzufügen, dürfen Sie nicht das `[TestMethod]`-Attribut zur Methode hinzufügen. Die auszuführende Methode wird vom Test-Explorer nicht registriert.


```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }

    // Thêm phương thức ToString() để in thông tin học sinh dễ dàng hơn
    public override string ToString()
    {
        return $"Id: {Id}, Name: {Name}, Age: {Age}";
    }
}

public class Program
{
    public static void Main()
    {
        // Khởi tạo danh sách học sinh
        List<Student> students = new List<Student>
        {
            new Student { Id = 1, Name = "Minh", Age = 21 },
            new Student { Id = 2, Name = "Phuc", Age = 15 },
            new Student { Id = 3, Name = "Thu", Age = 18 },
            new Student { Id = 4, Name = "An", Age = 20 },
            new Student { Id = 5, Name = "Nghi", Age = 22 }
        };

        // a. In toàn bộ danh sách học sinh
        Console.WriteLine("Danh sach toan bo hoc sinh:");
        students.ForEach(student => Console.WriteLine(student));
        Console.WriteLine();

        // b. Tìm và in ra danh sách các học sinh có tuổi từ 15 đến 18
        var studentsAge15To18 = students.FindAll(s => s.Age >= 15 && s.Age <= 18);
        Console.WriteLine("Danh sach hoc sinh co tuoi tu 15 toi 18:");
        studentsAge15To18.ForEach(student => Console.WriteLine(student));
        Console.WriteLine();

        // c. Tìm và in ra học sinh có tên bắt đầu bằng chữ "A"
        var studentsNameStartingWithA = students.FindAll(s => s.Name.StartsWith("A"));
        Console.WriteLine("Danh sach hoc sinh co ten bat dau bang chu 'A':");
        studentsNameStartingWithA.ForEach(student => Console.WriteLine(student));
        Console.WriteLine();

        // d. Tính tổng tuổi của tất cả học sinh
        var totalAge = students.Sum(s => s.Age);
        Console.WriteLine($"Tổng tuoi cua tat ca hoc sinh: {totalAge}");
        Console.WriteLine();

        // e. Tìm và in ra học sinh có tuổi lớn nhất
        var oldestStudent = students.Aggregate((s1, s2) => s1.Age > s2.Age ? s1 : s2);
        Console.WriteLine("Học sinh co tuoi lon nhat:");
        Console.WriteLine(oldestStudent);
        Console.WriteLine();

        // f. Sắp xếp danh sách học sinh theo tuổi tăng dần và in ra danh sách sau khi sắp xếp
        students.Sort((s1, s2) => s1.Age.CompareTo(s2.Age));
        Console.WriteLine("Danh sach học sinh sap xep theo tuoi tang dan:");
        students.ForEach(student => Console.WriteLine(student));
    }
}

# Learning-Scala
Learning Scala for CCA 175
import java.sql.DriverManager
import java.sql.Connection
import java.sql.Driver
import java.sql.SQLException

case class EmployeesCommission(first_name: String,
                                last_name: String,
                                salary: Double,
                                commission_pct: Double)
{
override def toString(): String = {
        "first_name: " + first_name + ";" + "last_name: " + last_name + ";" + " Salary: " + salary + "; " + "Commission: " + getcommissionamount() 
                                }
def getcommissionamount(): Any = {
        if (commission_pct equals 0.0) {"Not Applicable"}
        else {salary * commission_pct}
                                }


}
object CommissionAmount {
                        def main(args: Array[String]): Unit = {
                                val driver = "com.mysql.jdbc.Driver"
                                val url = "jdbc:mysql://nn01.itversity.com:3306/hr"
                                val username = "hr_ro"
                                val password = "itversity"

                Class.forName(driver).newInstance;
                val connection = DriverManager.getConnection(url, username, password)
                val statement = connection.createStatement()
                val resultSet = statement.executeQuery("Select first_name, last_name, salary,commission_pct from employees")

                while (resultSet.next()) {
                        val e = EmployeesCommission(resultSet.getString("first_name"),
                         resultSet.getString("last_name"),
                        resultSet.getDouble("salary"),
                        resultSet.getDouble("commission_pct"))
                println(e)
                                        }

                                                                }

}

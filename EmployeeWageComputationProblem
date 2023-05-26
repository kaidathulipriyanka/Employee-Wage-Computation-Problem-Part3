namespace EmployeeWageComputationProblem
{
    internal class Program
    {
        static void Main(string[] args)
        {
           interface IEmployeeWageComputation
        {
            public void addCompany(String companyName, int wagePerHr, int maxWorkingDays, int maxWorkingHrs);

            public void calculateTotalWage();

            public int getTotalEmpWage(String companyName);
        }

        class CompanyEmpWage
        {
        
            final String COMPANY_NAME;
            final int WAGE_PER_HR;
            final int MAX_WORKING_DAYS;
            final int MAX_WORKING_HRS;
            // instance variable
            int totalEmpWage;

            //parameterized constructor to get and set the values
            CompanyEmpWage(String companyName, int wagePerHr, int maxWorkingDays, int maxWorkingHrs)
            {
                COMPANY_NAME = companyName;
                WAGE_PER_HR = wagePerHr;
                MAX_WORKING_DAYS = maxWorkingDays;
                MAX_WORKING_HRS = maxWorkingHrs;
                totalEmpWage = 0;
            }

            void setTotalEmployeeWage(int totalEmpWage)
            {
                this.totalEmpWage = totalEmpWage;
            }

            @Override
            public String toString()
            {
                Console.WriteLine("Details of " + COMPANY_NAME + " employee");
                Console.WriteLine"-----------------------------------------------------");
                Console.WriteLine("Wage per hour:" + WAGE_PER_HR);
                Console.WriteLine("Maximum working days:" + MAX_WORKING_DAYS);
                Console.WriteLine("Maximum working hours:" + MAX_WORKING_HRS);
                return "Total wage for a month of " + COMPANY_NAME + " employee is " + totalEmpWage + "\n";
            }
        }

        class EmployeeWageComputation implements IEmployeeWageComputation
        {
    public static final int PART_TIME = 1;
        public static final int FULL_TIME = 2;
        // instance variables

        //references of companyempwage objects are stored in arraylist
        ArrayList<CompanyEmpWage> companies;
        //companyname is mapped with total employee wage
        HashMap<String, Integer> totalEmpWages;

        
        public EmployeeWageComputation()
        {
            companies = new ArrayList<>();
            totalEmpWages = new HashMap<>();
        }

 
        public void addCompany(String companyName, int wagePerHr, int maxWorkingDays, int maxWorkingHrs)
        {
            CompanyEmpWage company = new CompanyEmpWage(companyName, wagePerHr, maxWorkingDays, maxWorkingHrs);
            companies.add(company);
            totalEmpWages.put(companyName, 0);
        }

        int generateEmployeeType()
        {
            return (int)(Math.random() * 100) % 3;
        }

        int getWorkingHrs(int empType)
        {
            switch (empType)
            {
                case FULL_TIME:
                    return 8;
                case PART_TIME:
                    return 4;
                default:
                    return 0;
            }
        }

        public void calculateTotalWage()
        {
            for (CompanyEmpWage company : companies)
            {
                int totalWage = calculateTotalWage(company);
                company.setTotalEmployeeWage(totalWage);
                Console.WriteLine(company);
            }
        }

        int calculateTotalWage(CompanyEmpWage companyEmpWage)
        {
            Console.WriteLine("Computation of total wage of " + companyEmpWage.COMPANY_NAME + " employee");
            Console.WriteLine("-----------------------------------------------------");
            Console.WriteLine("%4s\t%4s\t%2s\t%4s\n", "Day", "Workinghrs", "Wage", "Total working hrs");

            int workingHrs, totalWage = 0;
            for (int day = 1, totalWorkingHrs = 0; day <= companyEmpWage.MAX_WORKING_DAYS
                    && totalWorkingHrs <= companyEmpWage.MAX_WORKING_HRS; day++, totalWorkingHrs += workingHrs)
            {
                int empType = generateEmployeeType();
                workingHrs = getWorkingHrs(empType);
                int wage = workingHrs * companyEmpWage.WAGE_PER_HR;
                totalWage += wage;
                Console.WriteLine("%4d\t%5d\t%10d\t%10d\n", day, workingHrs, wage, totalWorkingHrs + workingHrs);
            }
            totalEmpWages.put(companyEmpWage.COMPANY_NAME, totalWage);
            return totalWage;
        }

        public int getTotalEmpWage(String companyName)
        {
            return totalEmpWages.get(companyName);
        }

        public static void main(String args[])
        {
            EmployeeWageComputation employeeWageComputation = new EmployeeWageComputation();
            employeeWageComputation.addCompany("Microsoft", 4, 30, 100);
            employeeWageComputation.addCompany("Google", 5, 40, 170);
            employeeWageComputation.addCompany("Amazon", 19, 10, 150);
            employeeWageComputation.calculateTotalWage();
            String query = "Google";
            int totalWage = employeeWageComputation.getTotalEmpWage(query);
            Console.WriteLine("Total Employee Wage for " + query + " company is " + totalWage);
        }
    }

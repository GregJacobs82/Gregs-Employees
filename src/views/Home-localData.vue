<template>
    <div class="home">
        <!--
        <img alt="Vue logo" src="../assets/logo.png">
        <HelloWorld msg="Welcome to Your Vue.js App"/>
        -->
        <div class="small-container">
            <h1>Employees</h1>
            <EmployeeForm @add:employee="addEmployee"/>
            <EmployeeTable
                :employees="employees"
                @edit:employee="editEmployee"
                @delete:employee="deleteEmployee"
            />
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import HelloWorld from '@/components/HelloWorld.vue'
    import EmployeeTable from '@/components/EmployeeTable.vue'
    import EmployeeForm from "@/components/EmployeeForm";


    export default {
        name: 'home',

        components: {
            EmployeeForm,
            HelloWorld,
            EmployeeTable
        },

        data() {
            return {

                //todo: remove this after we get JSON API data working
                employees: [
                    {
                        id: 1,
                        name: 'Jimi Hendrix',
                        email: 'jimihendrix@example.com',
                    },
                    {
                        id: 2,
                        name: 'Oscar Wilde',
                        email: 'oscar@example.com',
                    },
                    {
                        id: 3,
                        name: 'Bill Murray',
                        email: 'billmurray@example.com',
                    },
                    {
                        id: 4,
                        name: 'Josh Miller',
                        email: 'joshmiller@example.com',
                    },
                ],
            }
        },

        methods: {
            /**
             * CREATE A NEW EMPLOYEE
             * @param employee
             */
            addEmployee(employee) {
                const lastId =
                    this.employees.length > 0
                        ? this.employees[this.employees.length - 1].id
                        : 0;
                const id = lastId + 1;
                const newEmployee = {...employee, id};
                this.employees = [...this.employees, newEmployee];
            },

            /**
             * EDIT EMPLOYEE
             * Take id and updatedEmployee parameters, map through the employees array, and update the correct employee.
             * @param id, updatedEmployee
             */
            editEmployee(id, updatedEmployee) {
                this.employees = this.employees.map(employee =>
                    employee.id === id ? updatedEmployee : employee
                )
            },

            /**
             * DELETE AN EXISTING EMPLOYEE
             * @param id
             */
            deleteEmployee(id) {
                this.employees = this.employees.filter(
                    employee => employee.id !== id
                )
            }
        }
    }
</script>

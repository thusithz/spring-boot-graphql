# Spring Boot GraphQL

Welcome to the **Spring Boot GraphQL** repository! 🚀 This project demonstrates how to use GraphQL with Spring Boot to build a scalable, high-performance API.

---

## 🌟 **What is GraphQL?**
GraphQL is a query language for APIs that provides a more efficient, flexible, and powerful alternative to REST. With GraphQL, you can:

- Fetch only the data you need.
- Combine multiple resources in a single request.
- Get predictable responses from your API.

For more details, visit the [GraphQL official documentation](https://graphql.org/).

---

## 📋 **Features**

- Built with **Spring Boot**.
- Implements a **GraphQL API** for querying and mutating data.
- Supports **in-memory H2 database** for easy testing.
- Ready-to-use sample schema and queries.

---

## 🛠️ **Technologies Used**

- **Java**: Backend programming language.
- **Spring Boot**: Framework for building production-ready Java applications.
- **GraphQL**: Query language and runtime for APIs.
- **H2 Database**: Lightweight, in-memory database.
- **Maven**: Build automation tool.

---

## 🚀 **Getting Started**

Follow these instructions to set up and run the project on your local machine.

### Prerequisites

- **Java 11** or higher installed.
- **Maven** installed.
- A code editor or IDE (e.g., IntelliJ IDEA, Eclipse).

### Installation Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/thusithz/spring-boot-graphql.git
   cd spring-boot-graphql
   ```

2. **Build the Project**:
   ```bash
   mvn clean install
   ```

3. **Run the Application**:
   ```bash
   mvn spring-boot:run
   ```

4. **Access the GraphQL Playground**:
   Open your browser and navigate to [http://localhost:8080/graphql](http://localhost:8080/graphql).

---

## 📝 **GraphQL Schema**

### Department Queries and Mutations
```graphql
type Query {
    departments: [Department]
    department(id: ID!): Department!
}

type Mutation {
    newDepartment(department: DepartmentInput!): Department
}

input DepartmentInput {
    name: String!
    organizationId: Int
}

type Department {
    id: ID!
    name: String!
    organization: Organization
    employees: [Employee]
}
```

### Employee Queries and Mutations
```graphql
extend type Query {
  employees: [Employee]
  employeesWithFilter(filter: EmployeeFilter): [Employee]
  employee(id: ID!): Employee!
}

extend type Mutation {
  newEmployee(employee: EmployeeInput!): Employee
}

input EmployeeInput {
  firstName: String!
  lastName: String!
  position: String!
  salary: Int
  age: Int
  organizationId: Int!
  departmentId: Int!
}

input EmployeeFilter {
  salary: FilterField
  age: FilterField
  position: FilterField
}

input FilterField {
  operator: String!
  value: String!
}

type Employee {
  id: ID!
  firstName: String!
  lastName: String!
  position: String!
  salary: Int
  age: Int
  department: Department
  organization: Organization
}
```

### Organization Queries and Mutations
```graphql
extend type Query {
    organizations: [Organization]
    organization(id: ID!): Organization!
}

extend type Mutation {
    newOrganization(organization: OrganizationInput!): Organization
}

input OrganizationInput {
    name: String!
}

type Organization {
    id: ID!
    name: String!
    employees: [Employee]
    departments: [Department]
}
```

---

## 📝 **Usage**

### Sample Query
To fetch data, you can use the following example query:
```graphql
query {
  departments {
    id
    name
    employees {
      firstName
      lastName
    }
  }
}
```

### Sample Mutation
To add new data, use this example mutation:
```graphql
mutation {
  newDepartment(department: { name: "HR", organizationId: 1 }) {
    id
    name
  }
}
```

---

## 🛡️ **Testing**

Run tests using Maven:
```bash
mvn test
```

---

## 🤝 **Contributing**

Contributions are welcome! Feel free to:
- Fork the repository.
- Create a new branch.
- Submit a pull request with your changes.

---

## 📬 **Contact**

- **Author**: Thusitha Kariyawasam
- **GitHub**: [https://github.com/thusithz](https://github.com/thusithz)

---

## 📜 **License**

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

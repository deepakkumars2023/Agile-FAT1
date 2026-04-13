STEP 1: CREATE MAVEN PROJECT

Create structure:

AgileLabFAT-Inheritance/
│
├── src/
│   ├── main/java/
│   └── test/java/
│
├── pom.xml
├── Dockerfile
🚀 STEP 2: WRITE JAVA CODE (INHERITANCE)
src/main/java/App.java
class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    Dog(String name) {
        super(name);
    }

    @Override
    void sound() {
        System.out.println(name + " barks");
    }
}

public class App {
    public static void main(String[] args) {
        Dog d = new Dog("Tommy");
        d.sound();
    }
}
🚀 STEP 3: WRITE JUNIT TEST
src/test/java/AppTest.java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class AppTest {

    @Test
    void testInheritance() {
        Dog d = new Dog("Tommy");
        assertTrue(d instanceof Animal);
    }
}
🚀 STEP 4: CREATE pom.xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
 http://maven.apache.org/xsd/maven-4.0.0.xsd">

 <modelVersion>4.0.0</modelVersion>

 <groupId>com.agilelab</groupId>
 <artifactId>inheritance-app</artifactId>
 <version>1.0</version>

 <properties>
   <maven.compiler.source>17</maven.compiler.source>
   <maven.compiler.target>17</maven.compiler.target>
 </properties>

 <dependencies>
   <dependency>
     <groupId>org.junit.jupiter</groupId>
     <artifactId>junit-jupiter</artifactId>
     <version>5.10.0</version>
     <scope>test</scope>
   </dependency>
 </dependencies>

 <build>
   <plugins>
     <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-surefire-plugin</artifactId>
       <version>3.2.5</version>
     </plugin>
   </plugins>
 </build>

</project>
🚀 STEP 5: RUN MAVEN (IMPORTANT)
mvn clean test
mvn package

✔ Must show BUILD SUCCESS

🚀 STEP 6: CONNECT TO GITHUB

Inside project folder:

git init
git add .
git commit -m "Initial commit - Inheritance project"
git branch -M main
git remote add origin https://github.com/deepakkumars2023/AgileLabFAT-Inheritance.git
git push -u origin main
🚀 STEP 7: MODIFY CODE & PUSH AGAIN

Example change:

System.out.println("Dog is barking loudly");

Then:

git add .
git commit -m "Updated code"
git push
🚀 STEP 8: CREATE DOCKERFILE
FROM eclipse-temurin:17
WORKDIR /app
COPY target/*.jar app.jar
CMD ["java", "-jar", "app.jar"]
🚀 STEP 9: DOCKER BUILD & PUSH
docker build -t deepakkumars2023/agilelabfat-inheritance:latest .
docker push deepakkumars2023/agilelabfat-inheritance:latest
🚀 STEP 10: CREATE JENKINS PIPELINE

Create new pipeline job → paste:

pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "deepakkumars2023/agilelabfat-inheritance:latest"
    }

    stages {

        stage('Checkout GitHub') {
            steps {
                git 'https://github.com/deepakkumars2023/AgileLabFAT-Inheritance.git'
            }
        }

        stage('Test using JUnit') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Build using Maven') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Create Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
🚀 STEP 11: RUN PIPELINE

👉 Click Build Now

✔ Should execute all stages

🧠 PART (b): INHERITANCE (WRITE THIS)
Animal is parent class
Dog is child class
Uses extends
Method overriding implemented
Demonstrates code reuse
📝 FINAL ANSWER (WRITE THIS EXACTLY)

A Maven-based Java application named AgileLabFAT-Inheritance was developed implementing inheritance using Animal and Dog classes. The code was tested using JUnit and pushed to GitHub. Jenkins pipeline was configured to automate Continuous Integration including stages for GitHub checkout, testing, building, Docker image creation, and pushing to Docker Hub.

🏆 FINAL RESULT

✔ Java app created
✔ Inheritance implemented
✔ JUnit testing done
✔ GitHub integration done
✔ Jenkins pipeline executed
✔ Docker image pushed

🔥 DONE

You can now:

✔ Execute from scratch
✔ Write full answer
✔ Explain confidently

If anything breaks, just send error — I’ll debug instantly 👍

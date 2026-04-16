# erd-tool-backend-common

ERD Tool 백엔드 서비스들이 함께 사용하는 공통 Java 라이브러리입니다.

포함 범위:

- `BaseEntity`
- `ApiException`, `ApiExceptionHandler`
- `HeaderConstants`
- `RequestCorrelationFilter`, `RequestCorrelationMdc`

## Build

```bash
gradle build --no-daemon
```

Java 21 기준으로 빌드합니다.

## Publish

기본 버전은 `0.1.0-SNAPSHOT`이며, 필요하면 `-PprojectVersion=0.1.0`처럼 덮어쓸 수 있습니다.

```bash
gradle publish \
  -PprojectVersion=0.1.0 \
  -Pgpr.user="$GITHUB_ACTOR" \
  -Pgpr.key="$GITHUB_TOKEN" \
  --no-daemon
```

GitHub Packages 좌표:

- Group: `com.erdcloud`
- Artifact: `backend-common`

패키지 저장소:

```text
https://maven.pkg.github.com/erd-tool/erd-tool-backend-common
```

## Consumer Example

```gradle
repositories {
    mavenCentral()
    maven {
        url = uri("https://maven.pkg.github.com/erd-tool/erd-tool-backend-common")
        credentials {
            username = findProperty("gpr.user") ?: System.getenv("GITHUB_ACTOR")
            password = findProperty("gpr.key") ?: System.getenv("GITHUB_TOKEN")
        }
    }
}

dependencies {
    implementation "com.erdcloud:backend-common:0.1.0"
}
```

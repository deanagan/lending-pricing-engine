# 🚀 Phase 1 — Scaffold the service

## Goal:

- Drogon server
- health endpoint
- loan pricing endpoint (stub)
- QuantLib wired in

## Step 1 — Install dependencies

macOS (brew)

```bash
brew install drogon
brew install quantlib
brew install cmake
```

## Step 2 — CMake setup

CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.16)
project(lending_quant_service)

set(CMAKE_CXX_STANDARD 17)

find_package(Drogon REQUIRED)
find_package(QuantLib REQUIRED)

add_executable(lending_quant_service
    src/main.cpp
    src/api/loan_controller.cpp
    src/quant/loan_pricer.cpp
)

target_link_libraries(lending_quant_service
    Drogon::Drogon
    QuantLib
)

```

## Step 3 - Drogon Server

src/main.cpp
```cpp
#include <drogon/drogon.h>

int main() {
    drogon::app().addListener("0.0.0.0", 8080);
    drogon::app().run();
}

```

Run:
```bash
mkdir build
cd build
cmake ..
make
./lending_quant_service

```

## Step 4 — First endpoint: health check

src/api/loan_controller.cpp
```cpp
#include <drogon/HttpController.h>

using namespace drogon;

class HealthController : public HttpController<HealthController> {
public:
    METHOD_LIST_BEGIN
    ADD_METHOD_TO(HealthController::health, "/health", Get);
    METHOD_LIST_END

    void health(const HttpRequestPtr &req,
                std::function<void (const HttpResponsePtr &)> &&callback) {
        auto resp = HttpResponse::newHttpJsonResponse(Json::Value("OK"));
        callback(resp);
    }
};

```

Test:
```
GET http://localhost:8080/health
```

## Step 5 — Loan pricing endpoint skeleton

```bash
POST /loan/price
```

This will:

- parse JSON
- map to domain model
- call quant layer
- return JSON

Wire this next.

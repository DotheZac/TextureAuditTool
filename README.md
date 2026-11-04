# Texture Audit Tool

Unreal Engine용 텍스처 검사 도구 · Texture auditing for Unreal Engine

**제작자 / Author:** DotheZac  
**지원 환경 / Supported environment:** Unreal Engine 5.7 · Windows 64-bit · Editor only  
**표시 언어 / UI language:** 한국어 에디터에서는 한국어, 그 외에는 영어 / Korean for Korean editor language; English otherwise

## 다운로드 / Download

배포 ZIP은 준비 중입니다. 배포가 시작되면 [Releases](https://github.com/DotheZac/TextureAuditTool/releases)에서 받을 수 있습니다. 이 저장소는 사용 안내와 피드백을 위한 공간이며, C++ 구현 소스를 포함하지 않습니다.

Distribution ZIPs are being prepared. Once available, download them from [Releases](https://github.com/DotheZac/TextureAuditTool/releases). This repository hosts documentation and feedback, not the C++ implementation source.

## 기능 / Features

- 폴더·경로 기준 Texture2D 검사 / Audit Texture2D assets by folder or path.
- 해상도, 압축, 알파, Mip, 스트리밍 설정 확인 / Inspect resolution, compression, alpha, mip and streaming settings.
- 현재 Editor 포맷과 허용 Mip GPU 메모리 확인 / Inspect actual Editor formats and allowed-mip GPU memory.
- 검토 순위와 권장 변경 표시 / Show review priorities and recommended changes.
- 다중 선택 권장 적용과 우클릭 수동 설정 / Apply recommendations to multiple assets or change settings manually.
- 우클릭으로 최초 변경 전 속성 복원, 프로젝트별 원래 설정 보관 / Restore pre-change properties from originals stored per project.
- 검토 상태·수정 기록, Undo/Redo, F5 새로고침 / Review records, modification history, Undo/Redo and F5 refresh.
- Reference Viewer·Content Browser 연동과 CSV 내보내기 / Reference Viewer, Content Browser and CSV export.

## 사용 안내 / User guides

- [한국어 사용 안내](docs/USER_GUIDE.ko.md)
- [English user guide](docs/USER_GUIDE.en.md)

검토 순위는 먼저 살펴볼 순서입니다. 위험 여부나 수정 개수를 의미하지 않습니다. 권장 변경은 텍스처의 실제 용도와 화질을 확인한 뒤 적용하세요.

Review priority indicates the suggested review order, not danger or the number of changes. Check the texture's intended use and visual quality before applying recommendations.

## 피드백 / Feedback

[버그 신고 또는 기능 제안 / Report a bug or request a feature](https://github.com/DotheZac/TextureAuditTool/issues/new/choose)

UE 버전, 플러그인 버전, 재현 순서, 기대 결과와 실제 결과를 알려주세요. 공개 게시판이므로 비공개 프로젝트 파일, 민감한 로그나 개인 정보를 첨부하지 마세요.

Include your UE version, plugin version, reproduction steps, expected behavior and actual behavior. Reports are public; do not attach private project files, sensitive logs or personal information.

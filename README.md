<img src="assets/logo.png" width="112" height="112" alt="ChunkSpan logo">

# ChunkSpan

Locate a fixed-width chunk including the final partial chunk. This Blyx library is part of the command-line tools collection.

A resumed batch can skip the final partial chunk when it treats a repeated acknowledgement as new progress. [Python, batching iterables](https://docs.python.org/3/library/itertools.html#itertools.batched)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-chunkspan.git
cd blyx-chunkspan
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-chunkspan) · [Package page](https://www.blyx-lang.space/packages/chunkspan) · [Handbook](https://doc.blyx-lang.space/guide/turnstone)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-chunkspan.git vendor/chunkspan
```

```blyx
use vendor::chunkspan::chunkspan;

fn main() {
    let size = 10.0;
    let width = 4.0;
    let index = 2.0;
    let result = chunkspan_bounds(size, width, index);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
8
10
3
```

## API

`chunkspan_bounds(size, width, index)`

Returns [start, exclusive end, chunk count]. Index equal to chunk count marks completion. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| size | A nonnegative exact integer |
| width | A positive exact integer |
| index | A nonnegative exact integer |

## In use

[Turnstone](https://github.com/Rahulchaube1/blyx-turnstone) uses this module to resume a chunked file job from acknowledged checkpoints.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-chunkspan/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).

# react-router-dom

## useNavigate()

- 변수를 선언한 뒤 해당 변수를 통해 함수를 호출하는 식으로 사용

  ```react
  function App() {
    // here!
    const navigate = useNavigate();
    function handleClick() {
      navigate("/");
    }
    return (
      <div>
        <button onClick={handleClick}>go home</button>
      </div>
    );
  }
  ```

- `navigate()`을 통해 페이지 이동을 하더라도 끝까지 실행됨

  ```react
  <button
    type="button"
    className="save-button"
    onClick={async () => {
      await commit(book.bookId, startDateTime);
  
      const updatedProgress = await recordProgress(
        book.id,
        book.bookId,
        userId,
        currPage,
        totalPage === currPage,
        stopReading,
      );
  
      if (stopReading) {
        openBottomSheet(GiveUpReading, '이번 책이 힘드셨나요?');
      }
  
      setCategory(updatedProgress.bookStatus);
  
      if (currentIsKkubook) {
        const { kkubookmode } = updatedProgress;
        const { level, kkubook_days } = kkubookmode;
        updateUserInfo({ level, kkubookDays: kkubook_days });
        if (currentLevel * 10 + currentKkubookDays === 99) {
          increaseComplete();
          navigate(`/congratulations/${updatedProgress.bookStatus}`);
          // return; 을 해주지 않으면 아래에 있는 조건문까지 모두 실행됨
        }
      }
      if (updatedProgress.bookStatus === 0) {
        navigate('/review');
      } else {
        navigate('/bookshelf');
      }
  }}
  >
    저장하기
  </button>
  ```

  